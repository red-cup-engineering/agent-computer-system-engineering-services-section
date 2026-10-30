# Design: actors, messages, resources as one typed model

Task: `task:design-actor-message-resource`. Design only — no code, test, or
README changes. All line numbers cite `planning-engine.mjs` as read for this
design (2026-09-10), version `0.3.0`.

## 1. What the house already decided (evidence, not invention)

The computer-data-engine specifications
(`lib/emsenn/services/561-group/services/engineering-services-section/services/computer-engineering-services-section/services/computer-data-engineering-services-section/apps/computer-data-engine/specifications/`)
already settle the question this task asks, at the house level:

- `protocol.schema.json`: *"The sole semantic network protocol: RMN terms and
  relational-field documents canonically encoded as CBOR and addressed by
  RFC 6920 `ni`. A2A, ActivityPub, CloudEvents, HTTP, MCP, and local IPC are
  carrier bindings only."* This is the house's own answer to "is a tool call,
  an AS2 activity, a CloudEvent, an A2A message, and an MCP call one thing":
  yes, and the one thing is not any of those formats — it is a canonical
  content-addressed message, and the formats are codecs.
- `message.schema.json`: an immutable envelope `{version, id: ni://, protocol,
  from: actor, to: actor, content: Thing | RelationalField, encoding:
  application/rmn+cbor}`. `id` **is** the NI of the canonical content — message
  identity is content identity.
- `actor.schema.json`: `{kind:"actor", address, capabilities, provenance}` —
  an actor is a bearer that can only act through an admitted capability;
  `resource.schema.json`: `{kind:"resource", address, resourceClass,
  provenance}` — addressable, classed, never acting.
  `actor-resource-field.schema.json` states the law directly: *"Every system
  participant... is an Actor relating to shared Resources through the one
  relational field. Role labels, sessions, and UI surfaces confer neither
  identity nor authority."*
- `capability.schema.json` / `capability-effects.schema.json` /
  `effect.schema.json` / `explicit-effect-boundary.schema.json`: the only
  boundary from computation to I/O is an actor presenting an admitted
  capability and resource, declaring an effect, and receiving a `receipt`
  or `refusal` from the **receiver** — never a self-report.
- `receipt.schema.json`: *"Receiver-produced evidence that a named effect or
  delivery condition occurred. A provider's report is not a receipt."*
- `refusal.schema.json`: a typed non-admission naming `{code, message,
  evidence}` — *"never becomes an exception-shaped hidden state."*
- `channel.schema.json`: transport "may fail, duplicate, reorder, or replay;
  only the relational field's identity and merge rules establish semantic
  convergence" — i.e., idempotence is not a transport property, it is a
  property of message identity plus the merge law.
- Glossary `actors.md`: actors are "distinguishable participants to which a
  system attributes actions... attribution does not erase the different
  authority and responsibility each kind can bear." Glossary `resource.md`:
  "an admitted role, not an assertion that the thing is expendable or owned."

This design does not re-derive these; it **binds** the planning engine's
existing kinds, predicates, and doors to them, and closes the one place the
engine's own mechanism falls short of what `channel.schema.json` requires
(§4).

## 2. What the engine does today, cited

**Actors and resources are already core kinds**, matching
`actor-resource-field.schema.json` structurally if not by field name:

- `actor` (line 206) / `resource` (line 207) are core kinds; `worker`,
  `office`, `collective`, `enterprise` extend `actor` (lines 226–227, and
  `collective`/`enterprise` nearby); `package`, `service`, `engine` extend
  `resource` (lines 208–210).
- `owned-by` (line 138, resource → actor), `located-at` (line 139, resource →
  literal, functional: "a path, URL, or NI"), `same-as` (line 73, any → literal:
  "an external identifier this entity also answers to... Content equality is
  not entity identity; this cell is the witnessed bridge") are the engine's
  addressing predicates, already distinguishing id / located-at / same-as the
  way `resource.schema.json`'s `address` plus house NI identity do.
- `capability` is a core kind (line 225: "the categorical signature of an
  action domain an agent can act on without supervision"), separate from the
  runtime `Capabilities` bearer-token class (line 2146) that actually gates
  writes. These are two different things sharing one name today — see §6.

**Attribution and authorization**: every write commits through
`Engine.commit` (line 869), which requires `by` to resolve to an existing
`worker`, `collective`, or `office` (checked inside `commit`, ~line 887) —
this is the attribution law. HTTP/MCP/A2A/inbox writes are additionally
gated by `Capabilities.authorize` (line 2146, method `authorize` further
down in that class): a bearer token names an actor, a tool allowlist, and an
optional container scope; `cap.actor` must equal `args.by` (capability
cannot author as someone else); scoped tokens are checked against each
tool's declared `scope` (`"cells"|"id"|"s"|"task"|...`, e.g. line 2080
`create_entity` scope `"cells"`, line 2094 `dispatch` scope `"task"`).
`mint({parent, ...})` implements attenuation: a child capability's tool list
must be a subset of the parent's, and its container scope cannot widen
(class `Capabilities`, method `mint`).

**Effect declaration**: the `effect` predicate (line 84) exists — *"A
declared effect of applying the operation... pure operations declare none"*
— but its domain is `operation` **entities** (declared via `declare_kind`/
ad hoc `operation:` records), not the 40-some built-in `TOOLS` (array
starting ~line 2080). Today no tool in `TOOLS` carries a machine-readable
effect list; the tool's `description` string is the only effect
documentation, and `READ_ONLY_TOOLS` (a `Set`, defined right after `TOOLS`)
is the only structured effect signal — a binary read/write flag, not a
per-operation state-change declaration. This is a real gap against
`effect.schema.json`'s requirement that every effect name actor, capability,
resource, kind, and receiver condition.

**Receipts**: `commit` returns `{tx, ni, stage, warnings}` (line ~911–912)
on success — this is already receipt-shaped (NI-addressed, receiver-produced,
since only the engine that holds the log can mint it) but does not carry the
house's `{kind:"receipt", effect, receiver, evidence}` field names.
**Refusals**: `AdmissionError` (line 649) carries `{errors, warnings}`;
`refusalFor`/`refusal()` (helper right after the `TOOLS` array, ~line 2122
and ~2156) shape it as `{refused: true, errors, warnings}` over MCP/HTTP.
Structurally close to `refusal.schema.json`'s `{kind, code, message,
evidence}` but missing a stable `code` and an `evidence` object — every
refusal today carries only prose strings.

**Causation chains**: partial and inconsistent across codecs today.
- CloudEvents: `POST /events` (~line 2793–2801) sets `"pe:causedby": ev.id`
  on the **result** event it returns, chaining a result to the event that
  caused it. `cloudEvent(tx, source)` (line 2267) does **not** set
  `pe:causedby` on ordinary transaction events, so the causal edge that would
  let a consumer replaying `/events` reconstruct "which prior tx licensed
  this one" (e.g., a `repair` on the `⊤` cell a prior `link` produced) is not
  emitted for the general case.
- AS2: `activity(engine, tx, base)` (line 2274) never sets `inReplyTo`,
  though AS2 defines it. A `repair` transaction targets a cell a prior `link`
  or `create` made contested; that lineage is derivable from `tx.increments`
  (`repair: true` increments carry `s,p,o` but not the causing tx id) but is
  not surfaced as `inReplyTo`.
- A2A: `/a2a` (~line 2850) reads `rpc.params.message.contextId` /
  `.taskId` off the **inbound** request and echoes them back in the result,
  but nothing ties an A2A `contextId` to the AS2/CloudEvents causation
  fields — three separate ad hoc correlation vocabularies (`pe:causedby`,
  `inReplyTo` unused, `contextId`/`taskId`) instead of one.
- MCP: no causation field at all; a `tools/call` result is a bare JSON-RPC
  reply keyed only by the RPC `id`, which the client does not persist.

**Outbox / inbox as views, never second owners** — this the engine already
gets right, and the design should state it as a law to preserve, not a gap
to fix:
- `/outbox` (line 2819–2822): `engine.store.txs.filter(...).map((t) =>
  activity(engine, t, base))` — a pure, stateless projection of the
  transaction log; nothing is written when `/outbox` is read.
- `/inbox` POST (line 2824–2835): `activityToToolCall(act, ...)` (line 2299)
  translates the inbound AS2 activity straight into a `{tool, args}` call and
  runs it through `guardedCall` (defined a few lines above the handler
  block, ~line 2716); the inbound activity itself is **never stored** — only
  the resulting transaction is. The `Accept`/`Reject` response the handler
  returns is synthesized from the tool result, not read back from a log.
- Same pattern for `/events` POST (executes `{tool, arguments}` and returns a
  derived CloudEvent, line 2793–2801), `/a2a` POST (line 2850, returns a
  synthesized A2A `Task` result), and `/mcp` POST (line 2841,
  `createMcpHandler` at line ~2364 runs `runTool` directly). **Every inbound
  door is a codec + `guardedCall`/`runTool`, never a second store.** This is
  exactly the "outbox/inbox as views over the log, never second owners" law
  the task asks for, and it already holds. The design in §5 keeps it.

**Idempotence — the one place the mechanism does not yet satisfy the law**:
`txName(tx) = "tx:" + niDigest(niOfValue(txBody(tx)))` (line 647) and
`txBody` (line 643) strips only `{tx, stage, verified}` before hashing — it
keeps `at` (the wall-clock ISO timestamp `commit` stamps at line 871,
`const at = now()`). Two calls carrying **the same message** (same `op`,
`by`, `increments`, `justification`) submitted a second apart get two
different `txId`s and are **both admitted** as distinct transactions,
because `at` is part of the canonical body being hashed. The **only**
existing replay guard is narrower: entity genesis with `id: "@ni"`
(`newId`, ~line 917–921) hashes `{e: null, kind, cells}` — excluding `by`
and time — and refuses a second identical genesis. There is no equivalent
guard for `link`, `update`, `attest`, `unlink`, `assert_cell`,
`create_batch`, or plain `create` with an explicit id. Replaying the exact
same `link` twice today produces two `tx:` entries and (harmlessly, because
witness is monotone in the FOUR order) the same cell value — but it is not
*inert* at the transaction layer: the log grows, `check`'s transaction count
changes, and two distinct NIs now claim to be "the" record of one message.
This is the concrete defect the codec/idempotence law in §4 closes.

## 3. The Message type

One typed model, over the engine's existing kinds (`actor`, `resource`,
`capability`, `operation`) plus the transaction envelope `commit` already
builds. A **Message** is the portable, codec-independent unit; a
**transaction** (`tx:`) is what a message becomes once admitted. They are
not two competing entities — see §7 for why messages do not also become log
*entities*.

```jsonc
// Message (JSON Schema 2020-12)
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://schemas.561.group/planning/message.schema.json",
  "title": "Message",
  "description": "The one typed unit every door (tool call, AS2 activity, CloudEvent, A2A message/send, MCP tools/call, HTML form post) is a codec of. Its ni is the identity a replay is checked against.",
  "type": "object",
  "required": ["ni", "actor", "capability", "operation", "arguments", "at"],
  "additionalProperties": false,
  "properties": {
    "ni": {
      "type": "string",
      "pattern": "^ni:///sha-256;[A-Za-z0-9_-]{42}[AEIMQUYcgkosw048]$",
      "description": "RFC 6920 digest of the canonical (RFC 8785 JCS) body: {actor, capability, operation, arguments, targets, correlationId}. Wall-clock time is NEVER part of this body (see law L2)."
    },
    "actor": {
      "type": "string",
      "pattern": "^(worker|office|collective):[a-z0-9][a-z0-9:._-]*$",
      "description": "Who: the attributed party. Must resolve to an existing worker, collective, or office at admission (Engine.commit, line 887)."
    },
    "capability": {
      "type": ["string", "null"],
      "description": "The bearer token (or null under an open/unscoped server) authorizing this actor for this operation. Verified and attenuation-checked before admission; never stored on the transaction itself — only its authorization VERDICT is (see Receipt.authorizedBy)."
    },
    "operation": {
      "type": "string",
      "description": "The tool name (one of TOOLS[].name) — the operation symbol Σ this message applies."
    },
    "arguments": {
      "type": "object",
      "description": "The bound slots of the operation's signature: the tool's inputSchema-shaped arguments, MINUS `by` (promoted to `actor`) and MINUS any capability/bearer material."
    },
    "targets": {
      "type": "array",
      "items": {"type": "string"},
      "description": "Resource/entity ids this message acts on or creates against (derived from the tool's declared `scope` argument, e.g. `id`, `s`, `task`, `cycle`, `scope`, `assignment` — see TOOLS[].scope, e.g. line 2080 create_entity scope 'cells', line 2094 dispatch scope 'task'). Used both for capability-scope containment (Capabilities.authorize) and for resource addressing."
    },
    "correlationId": {
      "type": ["string", "null"],
      "description": "The ni of a prior Message this one answers, replies to, or is caused by. Codec bindings: AS2 inReplyTo, CloudEvents pe:causedby, A2A taskId/contextId (see codec table, §5)."
    },
    "causationId": {
      "type": ["string", "null"],
      "description": "The ni of the Message whose ADMISSION directly produced the cell state this message reacts to (e.g. the create/link that put a cell at TOP, which THIS repair answers). Distinct from correlationId: correlation is conversational thread, causation is the specific antecedent transaction. Optional; when absent, equals correlationId."
    },
    "at": {
      "type": "string",
      "format": "date-time",
      "description": "Wall-clock receipt time, stamped by the receiving engine. NOT part of the ni digest (law L2) — this is envelope metadata, not message identity."
    }
  }
}
```

Laws:

- **L1 (attribution).** A Message with no `actor` resolving to an existing
  `worker`/`collective`/`office` is refused before any other check
  (mirrors `commit`, line ~887 today; already true, kept).
- **L2 (NI stability / idempotence).** `ni` is computed over
  `{actor, capability_verdict, operation, arguments, targets, correlationId}`
  — **excluding `at`**. Replaying byte-identical `{actor, operation,
  arguments, targets, correlationId}` through *any* door yields the same
  `ni`. This is the fix to the gap in §2: `txBody` (line 643) must exclude
  wall time from the identity computation the same way `id:"@ni"` genesis
  already does (line 917–919), generalized to every operation, not just
  `create`.
- **L3 (round-trip).** For every codec `C` in §5: `decode_C(encode_C(m)) =
  m` for every field the codec carries (a codec MAY be lossy only where the
  codec format itself has no slot — e.g. a bare HTML form post has no
  `correlationId` field, so it round-trips `correlationId: null`, not an
  error).

## 4. Idempotence law and its receipt

**The law the task asks for**: *every accepted message yields exactly one
transaction whose NI is derivable from the message; replaying the same
message admits nothing new.*

Mechanism (generalizing the existing `id:"@ni"` genesis-dedup, §2, to every
operation):

1. Compute `m.ni` per L2 the instant a message is decoded from any door,
   **before** running the tool.
2. Before calling `Engine.commit`, look up `m.ni` in a small NI→tx index
   (derivable, not a second store: a `Map` built once per `store.generation`
   the same way `Engine.cached` already memoizes derived reads, keyed by
   recomputing each existing tx's message-NI from its own `txBody` minus
   `at`).
3. **If found**: do not call `commit` again. Return the **same** Receipt
   that the first admission produced (§ Receipt, below), with
   `replay: true`. No new `tx:` line is appended. This is what makes replay
   *admit nothing new* — not "refuse the duplicate" (which would make
   retries brittle) but "answer with the receipt that already exists,"
   matching `channel.schema.json`'s framing that at-least-once delivery is
   normal and safety comes from identity + merge, not from the transport
   promising exactly-once.
4. **If not found**: admit normally through the existing `commit` (line
   869) unchanged, and index the new `tx` under `m.ni`.

This composes with the engine's existing monotone-witness merge (Belnap
FOUR, `witnessStep`, line ~24): even if two *different* messages happened to
assert the same cell, the cell's value is idempotent under that merge
already (asserting `t` twice keeps it `t`); L2/step 3 additionally makes the
**transaction count** idempotent under exact message replay, which today it
is not (§2).

## 5. Codec table

Every door already exists (§2); this table names the Message field each
carries, cites the current code, and states the round-trip law from L3.

| Format | Encode (format → Message) | Decode (Message → format) | Fields carried | Fields lost (round-trips to null) |
|---|---|---|---|---|
| **Tool call** (`call <tool> json`, `POST /api/call/{tool}`, `tools/call`) | `{tool, args}` → `operation=tool, arguments=args\{by}, actor=args.by, targets=args[scope]` | `{tool: m.operation, arguments: {...m.arguments, by: m.actor}}` | actor, operation, arguments, targets | correlationId, causationId (tool calls carry none today) |
| **AS2 activity** (`POST /inbox`, line 2299 `activityToToolCall`) | per `act.type` switch (line 2299–2321): `Create→create_entity, Update→update_entity, Delete→delete_entity, Add→link, Remove→unlink, Accept→attest, Invoke→{pe:tool,pe:arguments}` | `activity(engine, tx, base)` (line 2274): `type=AS2_OP[verb]` (line 2280 map), `actor=actorRef(by)`, `object=first increment`, `pe:increments=tx.increments` | actor, operation (via AS2_OP), arguments (via object/target), targets | **correlationId**: today NOT round-tripped — `activity()` never sets `inReplyTo`; design requires adding `act.inReplyTo = m.correlationId` (encode) and reading `act.inReplyTo` into `m.correlationId` (decode, alongside the existing switch in `activityToToolCall`) |
| **CloudEvent** (`GET/POST /events`, `cloudEvent()` line 2267) | `{data:{tool, arguments}}` → same as tool call, `correlationId` ← `ev["pe:causedby"]` if present | `cloudEvent(tx, source)`: `type=group.561.planning.<verb>, subject=first increment s, data.increments=tx.increments` | actor (`data.by`), operation, arguments, targets (`subject`) | **correlationId**: `cloudEvent()` (line 2267) does not currently emit `pe:causedby` on ordinary events — only the synthesized *result* event at line ~2799 does. Design requires `cloudEvent()` itself to emit `"pe:causedby": m.correlationId` when non-null |
| **A2A `message/send`** (`POST /a2a`, line 2850) | `parts.find(data).data` → `{tool, arguments}`, or text part `"tool {json}"` parsed by regex (line ~2855) | synthesized `Task` result: `contextId, id: taskId` | actor (`arguments.by` or `who.actor`), operation, arguments | **correlationId**: `taskId`/`contextId` already exist on the wire (lines ~2857–2860) but are **not** unified with AS2 `inReplyTo` / CloudEvents `pe:causedby` — design requires `taskId = m.correlationId ?? crypto.randomUUID()`, one field, not three vocabularies |
| **MCP `tools/call`** (`POST /mcp`, `createMcpHandler` line 2364) | `params.{name, arguments}` → `operation=name, arguments` | `{content:[{type:"text", text: JSON.stringify(result)}], structuredContent: result}` | actor (`arguments.by`), operation, arguments | correlationId: MCP JSON-RPC `id` is transport-local, not persisted; design requires echoing `m.ni` back as `structuredContent.ni` so a client can correlate a later `resources/read` of `planning://readout/{id}` to the message that produced it |
| **HTML form post** (`POST /kinds/{kind}` etc., `readForm()` ~line 2520) | form fields → `cells` object (via `fieldFor`/`createForm`, lines 2496–2536) → `{tool: create_entity\|update_entity, args: {kind, cells, by: actor}}` | server-rendered `page()` (line 2474) with a flash message, not a machine codec | actor (from `caller()`, cookie/`x-actor`), operation (implicit: which form), arguments (cells) | targets: only for the "create-and-attach" child forms (`childForm`, line 2635); correlationId/causationId: none — a human form post has no slot for either, correctly round-trips to null per L3 |

Codec laws each column must satisfy:

- **Round-trip (L3)**: encode then decode reproduces every field the format
  has a slot for. The table's "fields lost" column names exactly where each
  *current* codec implementation falls short of L3 for `correlationId`
  (AS2, CloudEvents, A2A) — three separate gaps with one shared design fix:
  route every codec's causal field through `Message.correlationId` /
  `causationId` instead of inventing a new ad hoc field per door.
- **NI stability**: every codec computes `m.ni` identically (L2) — a message
  submitted as a CloudEvent and, hypothetically, resubmitted as an MCP
  `tools/call` with the same `{actor, operation, arguments, targets,
  correlationId}` gets the **same** `ni` and the **same** idempotent
  outcome (§4). This is the concrete payoff of "one typed model": dedup
  works *across* doors, not just within one.

## 6. Capability: scope and attenuation

The `capability` **kind** (declared entity, line 225: "the categorical
signature of an action domain an agent can act on without supervision") and
the runtime `Capabilities` **class** (bearer tokens, line 2146) are two
different things today, both named "capability," and the design keeps them
distinct rather than merging them — they answer different questions (what
*kind* of action exists in the domain, vs. who currently *holds* a bearer
token for it):

```jsonc
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://schemas.561.group/planning/capability.schema.json",
  "title": "Capability",
  "description": "A bearer grant: actor, tool scope, optional container, attenuation lineage. Binds the house capability.schema.json (id, effects, resourceClasses) to the engine's tool/scope vocabulary.",
  "type": "object",
  "required": ["token", "actor", "tools", "issued"],
  "additionalProperties": false,
  "properties": {
    "token": {"type": "string", "description": "Bearer secret (Capabilities.mint, base64url random 24 bytes)."},
    "actor": {"type": "string", "description": "The one actor this token authorizes as (Capabilities.mint: 'attenuation cannot change the actor')."},
    "tools": {"type": "array", "items": {"type": "string"}, "description": "'*' or an explicit subset of TOOLS[].name. Effects = the union of the named tools' declared effect lists (§ effect gap, needs TOOLS[].effects — see recommendation below)."},
    "under": {"type": ["string", "null"], "description": "Container scope: resourceClasses in house terms, narrowed to 'this subtree of the entity graph' via Engine.descendants/parents (Capabilities.authorize)."},
    "parent": {"type": ["string", "null"], "description": "sha256(parent token).slice(0,16) — attenuation lineage, never the parent token itself (Capabilities.mint)."},
    "expires": {"type": ["string", "null"], "format": "date-time"},
    "revoked": {"type": "boolean", "default": false}
  }
}
```

Scope/attenuation law (already implemented, cited for completeness):
`mint({parent, tools, under})` (class `Capabilities`) requires: (a) actor
cannot change under attenuation; (b) child `tools` ⊆ parent `tools` unless
parent holds `"*"`; (c) child `under` cannot change once the parent has one.
`authorize(cap, tool, args, engine)` (same class) is the per-call check:
read-only tools always pass (`READ_ONLY_TOOLS`, a `Set` after `TOOLS`);
writes need the token to include the tool or `"*"`; `args.by` must equal
`cap.actor`; scoped tokens additionally require the tool's declared `scope`
argument (or, for `scope:"cells"`, one of a fixed anchor-predicate list) to
resolve inside `cap.under`.

**Gap to close in a future implementation (not this design's job to fix,
only to name)**: `capability.effects` per `capability-effects.schema.json`
is a list of effect ids. Today `Capabilities` tokens carry `tools` (tool
*names*), and `TOOLS[]` entries carry no `effects` field at all — only the
prose `description` and the binary `READ_ONLY_TOOLS` flag (§2). Recommend:
add `effects: string[]` to each `TOOLS[]` entry (e.g. `create_entity` →
`["entity.create"]`, `attest` → `["entity.complete","entity.fail",
"entity.abandon"]`), and derive `Capabilities.authorize`'s tool-scope check
from effect membership instead of tool-name membership, so a capability can
be attenuated to "may complete tasks but not fail them" — expressible in
`allowed-effect` (line ~/norm predicate, already used for duties) but not
today for bearer capabilities.

## 7. Receipt and Refusal

Every accepted message yields exactly one transaction (§4); every
transaction's admission result — success or refusal — is itself a Message
this design treats as **the receipt**, addressed by the *same* `ni`
mechanism, never a second parallel record:

```jsonc
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://schemas.561.group/planning/receipt.schema.json",
  "title": "Receipt",
  "description": "Receiver-produced evidence that a Message was admitted. Binds house receipt.schema.json {kind, effect, receiver, evidence} to Engine.commit's existing return shape (tx, ni, stage, warnings).",
  "type": "object",
  "required": ["kind", "messageNi", "tx", "effect", "receiver", "stage"],
  "additionalProperties": false,
  "properties": {
    "kind": {"const": "receipt"},
    "messageNi": {"type": "string", "description": "The Message.ni this receipt answers (§3, §4)."},
    "tx": {"type": "string", "pattern": "^tx:[A-Za-z0-9_-]{42}$", "description": "Engine.commit's txId (txName, line 647) — the transaction admitted, or the ORIGINAL tx on a replay (§4 step 3)."},
    "effect": {"type": "array", "items": {"type": "string"}, "description": "The effect ids actually produced: the cells this transaction's increments touched (tx.increments, e.g. line 908), read against TOOLS[].effects (§6 recommendation)."},
    "receiver": {"type": "string", "description": "The engine/actor that minted this receipt — today always the local engine instance; kept as a field for future federation."},
    "stage": {"type": "integer", "description": "tx.stage: the transaction's ordinal position in the log (Store.applyTx, line ~558)."},
    "replay": {"type": "boolean", "default": false, "description": "true when this receipt was returned WITHOUT a new commit, per idempotence law L2/§4 step 3."},
    "warnings": {"type": "array", "items": {"type": "string"}, "description": "Non-fatal admission warnings (e.g. checkDelegation's derivativity-unverified warning)."}
  }
}
```

```jsonc
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://schemas.561.group/planning/refusal.schema.json",
  "title": "Refusal",
  "description": "A typed non-admission, itself a Message (the sender's Message.ni is echoed so the refusal is addressable and correlatable). Binds house refusal.schema.json {kind, code, message, evidence} to AdmissionError (line 649).",
  "type": "object",
  "required": ["kind", "code", "message", "messageNi"],
  "additionalProperties": false,
  "properties": {
    "kind": {"const": "refusal"},
    "code": {
      "type": "string",
      "description": "Stable machine code. TODAY MISSING (§2): AdmissionError.errors (line 649) is prose only. Design requires classifying each AdmissionError throw site into a small closed code set, e.g. NOT_ACTOR, UNKNOWN_KIND, MISSING_REQUIRED, DOMAIN_RANGE, ACYCLIC, ALREADY_EXISTS, SCOPE_DENIED, NOT_GROUNDED, GOVERNANCE_INCOMPLETE, DELEGATION_UNBOUNDED."
    },
    "message": {"type": "string", "description": "err.errors.join('; ') — the existing prose (AdmissionError, refusal(), ~line 2156)."},
    "messageNi": {"type": "string", "description": "The Message.ni this refusal answers — lets a refusal be replayed/dedup'd exactly like a receipt (§4): resubmitting the same malformed message twice returns the same refusal, not two."},
    "evidence": {"type": "object", "description": "Structured detail: which cell/predicate/tool argument failed (e.g. the specific ⟨s,p,o⟩ a repair-on-non-⊤ refusal names, commit() ~line 894)."}
  }
}
```

Law: **a refusal is also a message** — it is addressed by `messageNi`
exactly as a receipt is, so a client that resubmits a message that will
fail again gets the *identical* refusal rather than a fresh, differently
worded one each time (today: `AdmissionError`'s message text is
regenerated fresh from live state on each attempt, which is fine when the
state hasn't changed but means a refusal is not currently NI-stable the way
a receipt would be under §4 — this design extends L2's dedup index to
refusals too, keyed by the same `messageNi`).

## 8. Causation chains

Already covered per-codec in §5's table; the unifying design decision is:
**one field pair on the Message (`correlationId`, `causationId`), three
codec bindings, not three vocabularies.**

- AS2 `inReplyTo` ← `correlationId` (currently absent from `activity()`,
  line 2274 — add it).
- CloudEvents `pe:causedby` ← `correlationId` (currently only set on the
  synthesized `/events` POST result, line ~2799 — extend `cloudEvent()`
  itself, line 2267, so every transaction event carries it when the
  originating message had one).
- A2A `contextId`/`taskId` ← `correlationId` (currently present but
  disconnected from the other two — unify by deriving `taskId` from
  `correlationId` when supplied, generating one otherwise, exactly as
  `/a2a` already does for `crypto.randomUUID()` fallback, line ~2860).
- A `repair` transaction's `causationId` is the `tx:` id of the transaction
  whose witness first put the cell at `⊤` — derivable today from
  `cell.history` (`Store.applyWitness`/`applyRepair`, lines ~583–593) by
  walking back to the last `history` entry with `value: FOUR.TOP` before
  this repair; the design requires this be computed once by `commit()` and
  stamped into the tx's own `causationId` field rather than left for every
  consumer to recompute.

## 9. Outbox/inbox as views; dispatch as a Message; addressing

**Outbox/inbox are views, never second owners** — restated as a law, holding
today (§2 evidence): no inbound door persists the inbound envelope; every
door decodes to a Message, runs `guardedCall`/`runTool`
(`guardedCall` ~line 2716, `runTool` line ~2143), and the **only** thing
that persists is the resulting `tx:` line the log already owns. `/outbox`
and CloudEvents `GET /events` are the reverse view: pure maps over
`engine.store.txs`. This design changes nothing here except requiring the
NI-dedup index of §4 to sit *beside* `store.txs` as a derived cache (like
`Engine.memo`, line ~665) — never a competing log.

**Actors' inboxes as dispatch/assignment**: `actorDocument()` (line 2293)
already exposes `inbox: base + "/inbox"` per actor, but that inbox is
*global* — every actor's inbox is the same `/inbox` endpoint, disambiguated
only by the AS2 activity's `actor` field, not scoped per-recipient. The
engine's actual per-actor "inbox" — work waiting for a specific actor to
act — is `assignment` (kind, line 230: "assigns-task, to-worker,
from-dispatcher, authority-bound") produced by `dispatch()` (Engine method,
~line 1127) and read back via `next_work` (tool, filters by `worker`,
~line 2109) and the `holds` field on a worker's `read_entity` reading (line
2004: tasks assigned via `to-worker`, not yet `revoked-at`). Design: model
**dispatch as a Message** whose `operation="dispatch"`, `actor=dispatcher`,
`targets=[task]`, `arguments={worker, authorityBound}` — then "an actor's
inbox" is simply *the derived view* `{m : Message | m.operation=="dispatch"
∧ worker(m) == this actor ∧ not revoked}`, i.e. exactly what `next_work`
already computes from `assignment` entities today. No new mechanism is
needed; the AS2 `Invoke` activity type (line 2320, `case "Invoke"`) is
already the generic escape hatch for "any tool call" and could carry
`pe:tool: "dispatch"` — but a dedicated AS2 activity type for dispatch
(house AP conventions sometimes use `Offer`/`Flag`) is not required; `Invoke`
with `pe:tool:"dispatch"` already round-trips correctly per §5's table.

**Resource addressing** (id, NI, located-at, same-as — the four already in
the ontology, §2):

| Field | What it identifies | Predicate/mechanism | Functional? |
|---|---|---|---|
| `id` | The entity as a stable name in *this* log (`kind:slug`) | `newId()` (Engine method, ~line 917) | yes, one id per entity |
| NI (`pe:genesis`) | The content digest of the entity's **genesis** cells (its first `is-a` witness's transaction) | `entityNode()` (line 2247): `node["pe:genesis"] = "ni:///sha-256;" + genesis.tx.slice(3)` — reads the tx NI of the FIRST history entry on the entity's `is-a` cell | derived, not stored |
| `located-at` | Where the resource's *content* actually lives outside the log: a path, URL, or an NI of that external content | predicate, line 139, functional | yes |
| `same-as` | Every external identifier this entity also answers to (a migrated record's old id, a URI, a ticket, a digest) | predicate, line 73, non-functional, multi-valued | no — multi |

Law: `id` is a **name** (may be renamed only by `supersedes`, line 71,
never mutated in place); NI is **content identity** of the genesis
transaction (never changes, since genesis is written once); `located-at` is
**where to fetch the current content** (may be superseded via `update`,
being `functional: true`); `same-as` is the **witnessed bridge** to
identifiers this entity did not mint itself. A Message's `targets` field
(§3) should resolve through `id` first (the log's own namespace) and fall
back to `same-as` lookup (`Store.subjects("same-as", targetString)`) only
when a codec hands the engine an external identifier it does not recognize
as an `id` — this is exactly what `/import.ndjson`'s existing id-resolution
already does at the boundary (`decodeURIComponent`, ~line 2775–2785) and
this design generalizes it to every inbound codec, not just NDJSON-LD.

## 10. Should messages be first-class log entities? (cost/benefit, doubling)

**Recommendation: no — a Message is a *view* over a transaction plus its
originating door, never a stored entity of kind `message`.**

Cost of making messages first-class entities:
- **Doubling.** Every write would produce two log lines: the `tx:` the
  operation already commits (line 908–911) and a second `message:` entity
  wrapping/pointing at it. The relation between them (`message` yields
  `tx`, or `tx` `same-as` `message`) would itself need admission, cost, and
  a schema — pure overhead over what `tx.increments` plus the codec-decode
  step already carries.
- **Identity confusion.** `message.schema.json` already makes `id` the NI of
  canonical content. If Message became a stored entity with its own
  `kind:slug` id (per `newId()`, ~line 917) it would have *two* identities —
  a log-namespace id and a content-NI — for one thing, which is precisely
  the confusion `same-as`'s doc string (line 73: "content equality is not
  entity identity") warns against introducing.
- **Retention weight.** Every `create_entity` etc. call today is exactly
  one `tx:` line (JCS-canonical JSON, line 908). Doubling that with a
  `message:` entity roughly doubles log bytes for the identical information
  content, since a transaction already carries `by`, `op`, `increments`,
  `at`, `justification`, `note` — everything a Message needs (§3) minus the
  `capability`/`correlationId` fields, which are a small, cheap addition to
  the transaction envelope, not a reason to duplicate the whole record.

Benefit claimed for first-class messages (and why it is already available
without them): "so a message can be addressed/queried directly." It
already can be: `tx:` **is** addressable (`GET /activities/{tx}`, line
2837), queryable (`engine.store.txs`), and NI-verified on every fold
(`Store.applyTx`, line 559: `tx.verified = txName(tx) === tx.tx`). Adding
`correlationId`/`causationId`/`capability` as three more optional fields on
the existing transaction envelope (alongside `note`, `justification`, which
are already optional fields added the same way, lines 872–873) gets every
benefit §3–§8 need without a second kind, a second id space, or a second
persisted copy.

**The one place a message needs to be addressable *before* it produces a
transaction** is a refusal (§7): a message that fails admission produces no
`tx:` at all today (an `AdmissionError` is thrown and never appended,
`commit()` line ~906 `if (errors.length) throw...` — nothing is written to
`this.store`). Recommendation: refusals stay **out of the append-only work
ledger** (a refusal is not work; the README's "Doors" section already frames
the log as "the work ledger" — refusals are not admitted work) but the
NI-dedup cache of §4 step 3/§7 keeps them in the same in-memory derived
index as receipts, keyed by `messageNi`, evicted on process restart (a
resubmitted message after restart re-attempts admission fresh — acceptable,
since a refused message changed nothing to persist in the first place).

## 11. Summary of what this design requires of a future implementation

Ordered by dependency, not priority (all are outside this task's scope —
design only):

1. Exclude `at` from the NI computation of every `commit()` (generalize
   `txBody`, line 643, or add a parallel `messageBody` that both `txName`
   and the new dedup index use) — closes §2's idempotence gap, realizes L2.
2. Add an in-memory `messageNi → {tx, receipt}` index, generation-keyed like
   `Engine.memo` (line ~665) — realizes §4's replay law without touching the
   append-only log's format.
3. Add `correlationId`/`causationId` (optional) to the transaction envelope
   `commit()` builds (alongside `note`/`justification`, lines 872–873), and
   thread them through `activity()` (line 2274 → `inReplyTo`), `cloudEvent()`
   (line 2267 → `pe:causedby`), and `/a2a`'s `taskId`/`contextId` handling
   (~line 2857) — closes §5/§8's three-vocabularies gap.
4. Add `effects: string[]` to each `TOOLS[]` entry and derive
   `Capabilities.authorize`'s scope check from effect membership — closes
   §6's gap, makes `capability.schema.json`'s `effects` field real here.
5. Classify `AdmissionError` throw sites into the closed `code` set named in
   §7's Refusal schema.
6. Do **not** add a `message` kind to `CORE_KINDS` (§10).

## Provenance

- `planning-engine.mjs` (2,900+ lines), read in full for: NI/JCS (lines
  1–58), ontology/predicate table (lines 60–330), `Store`/`Engine`/`commit`
  (lines 497–1210), `Capabilities` (line 2146), `TOOLS` array and
  `READ_ONLY_TOOLS` (~2080–2125), INTERCHANGE section — `jsonLdContext`,
  `entityNode`, `cloudEvent`, `activity`, `actorDocument`,
  `activityToToolCall`, `agentCard`, `openApi` (lines 2236–2358), MCP
  handler (lines 2364–2415), HTML door and web handler including
  `/inbox`/`/outbox`/`/events`/`/a2a`/`/mcp` (lines 2474–2870).
- `README.md` beside the engine (theory-to-mechanism table, doors table,
  authority section).
- House specifications:
  `.../computer-data-engineering-services-section/apps/computer-data-engine/specifications/{actor,resource,actor-resource-field,operation,statement,message,channel,protocol,capability,capability-effects,effect,explicit-effect-boundary,receipt,refusal,evidence,thing,relational-field}.schema.json`.
- Glossary: `.../engineering-services-section/content/text/glossary/terms/{actors,resource}.md`.
- Repo search for prior ActivityPub/A2A/CloudEvents/ocap decisions: the
  decisive prior decision is `protocol.schema.json`'s explicit statement
  that A2A/ActivityPub/CloudEvents/HTTP/MCP are carrier bindings over one
  semantic protocol; no separate object-capability theory note was found
  outside the `capability*.schema.json` family above.
