# Simple Planning Engine

One Node file, `node:` modules only, no imports from the rest of this tree. It
holds the planning data for working on the rest of the codebase, so working on
the codebase cannot break it.

Bookmark: **http://127.0.0.1:7331/** — served by the user systemd unit
`simple-planning-engine.service` (in this directory, linked into
`~/.config/systemd/user/`, enabled, restarts on failure, survives reboots).

```
node planning-engine.mjs mcp        # MCP over stdio (Claude: .mcp.json `planning`; Codex: .codex/config.toml `planning_engine`)
node planning-engine.mjs web        # HTML forms + every HTTP door on 127.0.0.1:7331
node planning-engine.mjs serve      # both
node planning-engine.mjs call next_work '{"worker":"worker:claude"}'
node planning-engine.mjs call self '{}'         # what this engine is, live
node planning-engine.mjs call describe_self '{"by":"worker:claude"}'  # …and into the log
node planning-engine.mjs schema task            # JSON Schema of a kind
node planning-engine.mjs merge other.jsonl      # G-set union of another log by transaction NI
node planning-engine.mjs mint --actor worker:codex --tools attempt,attest --under plan:build
npm test
systemctl --user restart simple-planning-engine.service   # after changing the file
```

Data: `data/planning.jsonl`, an append-only NDJSON witness log (override with
`PLANNING_ENGINE_DATA`). Capability tokens: `data/secrets/capabilities.jsonl`
(gitignored). Several processes share one log; each folds new lines before
every operation. The log is the **work ledger**; every door below is a
**protocol tile** over it. The log is **not** in git: `data/planning.jsonl` is
gitignored, so the running service's state is the ledger itself, and the only
way another checkout gets it is `merge`.

## The theory it implements

Sources are in the science section under
`lib/emsenn/services/561-group/services/science-services-section/`. The engine
is a model of these carriers; where it simplifies, the README says so.

| Theory (carrier) | What the engine does with it |
| --- | --- |
| **Theory of work** (work-science `triage/what-is-the-theory-of-work.md`): sorts State, Cost, Capability; work-acts with positive cost; cost quantale with composition and parallel laws; the endeavor monad; intention fibration; failure-fibre decomposition; capability update through failure; learning-rate functor; bottleneck | Cells are the state; `cost` lives in ([0,∞], +); a container's reported cost is the Σκ upper bound the two laws license and its `cheapestSuccess` is the sum over the **distinct** nodes of the cone, each paid once: revisiting a component already counted returns the quantale identity 0, not "unknown", so a subtask shared by two parents is neither charged twice nor allowed to nullify a known cost (the Lawvere distance). An **attempt** is an intention token (intends, realised, outcome). A worker's **budget** κ̄ and a task's **estimated-cost** κ̃ make Proposition 8 computable: reachability is "an alternative act within budget", suboptimality is "not the cheapest to that realised target", and the Reason cell (lapse / mistake / slip / violation) follows the eight-cell table. `bottleneck(worker)` is "ready work exists but none fits the budget". Practice counts accumulate over failed attempts too (Cor. 5.2); the learning rate Λ is the sequence of cost deltas and mastery its fixpoint (Thm 7); `expected_cost` is κ̃(C, task) from the worker's own practice. Invariant 2 (κ > 0) is not enforced at admission: cost 0 is how an aborted token is recorded. The organisational form realized is the authority-dispatched one of Theorem 10 (a hard refusal, not a ρ* cost); the other three forms are not expressible. |
| **Endeavor** (glossary `endeavor.md`, `campaign.md`, `phase.md`, `workflow.md`, `priority.md`) | enterprise ⊃ endeavor ⊃ campaign ⊃ project ⊃ plan ⊃ task ⊃ work-item (work-unit or workflow), with goal, objective, milestone, charter. An endeavor's readout lists its **absorbed** failed components: failure does not end it (the Kleisli flattening); only abandonment or a failed aim does. The readout names that absorbed set and nothing else: no field stands in for a functor the code does not implement. A campaign must carry `horizon-ends`; its **front** is the gap to the objective: remaining tasks, remaining estimated cost, what is ready now, and whether it advanced, held, or retreated since the last observation. |
| **Algebraic structure of work** (`notes/algebraic-structure-of-work.md`) and **operation as morphism** (computer-data-engine `operation.schema.json`) | An `operation` is a symbol of the signature Σ with typed `slot`s (`reviewer:worker`, `document:resource`), an `effect` list, `yields` as its codomain, and `branching`. A task, work item, or work unit that names an operation is a **term**; its `parameter` cells (`slot=value`) are the substitution. `term` reports bound, open, and ill-typed slots and whether the term is ground; when an operation is present the work type is read off the term (open → derivation; ground → process, or procedure if the operation branches) instead of the declared nuclei. |
| **Roadmap science** (`roadmap-science-services-section/README.md`; ruling 2026-09-06 "roadmaps are derived from journaled work, never handwritten"; `derive-roadmap-readout`) | `roadmap` (tool, `/roadmap`, MCP resource `planning://roadmap`) is a `RoadmapReadout` folded from the record: one lane per enterprise or top-level endeavor, one cell per parent with its tasks by horizon and ready / active / blocked / done counts, each task's open **saturation slots** (who, when, produced: what dispatch and execution have not yet closed), its roles, milestones with a derived horizon (the latest horizon among their unsettled requirements) read against `target-date`, dated commitments (`horizon-ends`, `deadline`, `target-date`) banded by calendar and compared with the derived horizon, **drift** wherever the two disagree, cross-lane dependencies (what makes it one roadmap), and coherence findings: orphan tasks, loose containers, unserved objectives, empty milestones, duplicate titles not settled by `supersedes`. Nothing on it is stored. |
| **Predicate category** (math `predicate.md`, `predicate-category.md`; `subject-predicate-object.md`) | Predicates are objects of a small category whose generators are specialization, converse, and the two projections. A declared predicate may `specializes` another (a sub-relation: its domain and range must lie within the parent's, and every cell of it is read as a cell of the parent, so `deploys specializes acts-on` puts `deploys` in the acts-on **family**) or be the `converse-of` another (read backwards, never stored twice). `kind_category` lists families, specializations, and converses; `read_entity` shows each cell's `readAs` chain. |
| **Actors and resources** (engineering `actors.md`, `resource.md`; information-science `informational-resource.md`; computer-data-engine `actor-resource-field.schema.json`; `package.md`, `service.md`, `engine.md`) | `actor` and `resource` are core kinds. Actors bear capabilities and can be attributed, bound, and served; resources are addressable things work acts on and cannot act. worker, office, collective, enterprise extend actor; **package** (boundary signature Σ, `exports`), **service** (`interface`, `provided-by`), **engine** (`holds-state-in`) extend resource. Work carries ActivityStreams roles: `acts-on` (object), `targets`, `uses` (instrument), `yields` (result), `for-party` (beneficiary), `performed-by` (actor). `resource_graph` closes roles with `part-of`, `requires-resource`, `owned-by`, `provided-by`, and capability edges around any entity. |
| **Ontology as data** (`schema.md`; office schema pattern: one schema, many validated instances) | Kinds and predicates are declared in the log. `declare_kind` (an entity of kind `kind` that `extends` an existing kind; instances inherit predicates, required cells, and derived readings from the nearest core ancestor) and `declare_predicate` (domain, range, functional, acyclic, specializes, converse-of). Declarations are witnessed and justified when revised; a kind with instances or subkinds and a predicate with live cells cannot be retired; `check` reports cells that a revised declaration no longer admits instead of dropping them. `customer extends actor`, `deploy-task extends task`, `dataset extends resource` are one call each. |
| **Duties** (agency `duties/*.json`, `works/*.json`; office `deontic-profile`) | A duty is a MUST norm with `correlative` (the claim-holder), `receiver-condition` (what must be accepted for discharge), `allowed-effect`s, `requires-capability`, and `delegable`; an office carries a `deontic-profile` (work = duty, liberty, deontic-power, deontic-immunity). |
| **Merge as a lattice join** (settled note D3/D4) | A cell is a multi-value register over the FOUR base: `witnessed` is the join of every witness, `repairs` is a set of `{tx, to, over}` events where `over` names the repairs the writer had already folded, and the value is the witnessed join when no repair survives, the common target when the survivors agree, and ⊤ when they disagree. Union, set difference by name, and the FOUR join are each commutative, associative and idempotent, so `merge` is a least upper bound: `merge(A,B)` and `merge(B,A)` agree on every cell, `merge(A,A) = A`, and two forks that repair one contested cell in opposite directions both read ⊤. A merge absorbs foreign facts without re-running admission, so what could not have been submitted locally is reported by `check().mergeAnomalies` rather than refused: data, not an error. |
| **Formal planning theory** (`notes/formal-planning-theory.md`) | Finite tasks under a strict partial order `depends-on` (cycles refused), means-end warnings, a refinement measure; revision, abandonment, retirement, and repair require a justification; abandoning a plan abandons its unsettled components. |
| **Predicated work** (`predicated-work-services-section`) | Every change is a witness on a cell valued in Belnap's FOUR; values are monotone in the knowledge order; ⊤ is a repair condition; completion is quiescence at the goal cells; a completed-by and a failed-by witness cannot coexist without an explicit contest; a parent's completion is derived and reported as derived; workflows report sequence/branch/parallel patterns (`gated-by` carries the branch condition), liveness, dead items, structural soundness, and instance completion; one workflow nests inside another as ⟨workflow `contains` work-item⟩ together with ⟨work-item `realized-by` workflow⟩ — `contains` cannot range over a workflow — and whichever cell closes that nesting is refused with `BOUNDARY_TYPE` when both workflows declare a `boundary-type` and the two differ, an absent one being ⊥ and never refusing; that is typed composition, not a monoidal category, since no tensor exists; the six-phase loop is gated in order on a cycle and `produces-seed-for` links cycles. Capability fit is the meet of the **capability fusion semilattice** (office ⊙ requirement, f absorbing), of which `requires-capability` is the requirement side — a semilattice, not a fibre bundle; a direct negative witness against an office-derived capability reads ⊤ unless the negative witness was justified. The three strata of a cell (asserted, saturated, settled) and its evidence pair (support, refutation) are derived, never stored. |
| **Theory of governance** (lakota section `questions/what-is-the-theory-of-governance.md`) | A **norm** needs attribution (a collective or office), binding (members), and becoming: the subject's fiber gains ⟨subject, governed-by, norm⟩. Deontic operators are derived from the force (MUST = O, MAY = P, MUST NOT = F, SHOULD = O with a justified deviation); when the subject is a collective the cell is read once per member and the readings meet; a norm's **operativity** is the knowledge meet of its three judgments. A `MUST NOT performs` norm restricts dispatch fit (□_R on the capability fiber). Founding is a constituent act attributed to a founder. |
| **Dispatch and delegation** (FARS §12) | An **assignment** is its own entity with boundedness, derivativity, accountability non-transfer, revocability; a task holds one assignee unless the dispatcher forces co-assignment; an office admits `seats` incumbents. |
| **Modality, horizon, force** (spec 2026-09-04) | The four-corner cell: work type and modality are read from the two nuclei (meaning-settled σ, execution-settled Δ); horizon is causal height in the dependency cone (0 Now, 1 Soon, 2 Later, ≥3 or blocked Eventually); `concordance` reports whether the founder's rule (modality → horizon) agrees with the causal reading. Milestones are derived, never asserted. |
| **Quartet recurrence / nuclear pair** (Obsmetrologia, `keystone-conflation.md`) | Two readings share the name σ/Δ and `settlement(id)` reports both plus whether they agree. The **derived** pair: σ (the entity's own fiber has saturated), Δ (its output has transferred downstream), H = σ ∧ Δ, and the corner (stable / potential / active / absurd). The **declared** pair: the `meaning-settled` and `execution-settled` cells a worker witnessed. `concordance` reconciles them exactly as the horizon readings are reconciled; a disagreement is reported, never silently resolved. |
| **Four-regime dichotomy** (`regime-of-task`, `completion-as-quiescence`) | `closureOrdinal(id)` computes κ from the cone: finite depth → strict; a recurrent practice in the cone → ω; aggregation over cycles → transfinite-bounded; an aim without a finite milestone set → aperiodic. Stages are ordinals ω·c + k over closed cycles. The four regime names are labels for those four shapes: nothing compares them, and no ordinal comparator is implemented. |
| **NI addressing** (`ni-services-section`, `semantic-content-identity.mjs`, `eavt.mjs`, `cell.md`) | **Transaction identity** is evidence that an act occurred at a time: `tx:<digest>`, the NI (RFC 6920, sha-256, base64url) of the RFC 8785 canonical body, wall time included; replay verifies every name and `check` lists tampering. **Message identity** is a second, distinct identity: `msg`, the NI of `{actor, operation, arguments, targets, correlation}` with wall time excluded. Submitting the same message twice through any door appends one transaction and answers the second with the first's receipt and `replay: true` — so two byte-identical write calls collapse into one, and an operator who wants two alike events recorded (the same `record_event` twice) varies the `note`. Across a merge the receipt names the earliest transaction under `(at, tx)`. `correlation` is the one causal field, spoken as AS2 `inReplyTo`, CloudEvents `pe:causedby`, A2A `taskId`/`contextId`, and MCP `structuredContent.msg`; causation itself is derived from the cell's history, never stored. An entity created with `id: "@ni"` is constituted by the digest of its genesis cells with the subject held null. Names stay human (`kind:slug`) and point at NIs (`pe:genesis` in JSON-LD). |
| **Schema as category** (feltos `contract.mts`, metroplat `structural.mts`, `realize.mts`, jsnode `type-flow.mts`) | `kind_schema` derives a JSON Schema per kind from the predicate table (the free direction; the ontology's declared ranges are the choices); `kind_category` reads the kind category off the same table: kinds as objects, entity-ranged predicates as morphisms, initial and terminal kinds under containment, reachability, functional predicates as partial functions, coproduct ranges (`realized-by: work-unit | workflow`), hubs, orphans; `validate_cells` checks a candidate against a kind's schema. |
| **Gurwitsch field / zipper** (`macrofocus.md`, `refocusing.md`) | `focused-on` is a worker's designated element; `refocus` is a witnessed supersession. |
| **Role fibration / enrollment** (`enrollment.md`) | `holds-office` is a section: one incumbent per seat. |
| **Tracking, review, feedback** (`observation`, `finding`, `adjustment`) | Observations live in their own fiber and carry the front so movement can be read; findings are first-class, and a review is one act — container, findings, and the `contains` links ride one transaction, so a refused finding refuses the whole review and leaves no empty container behind; adjustments carry a loop type. |

Known simplifications: states are cells rather than a typed state category, so
the intention fibration is realized nominally; parallel cost gets the Σ bound
rather than a separate treatment; a kind or predicate declared in a transaction
is usable from the next transaction on, so a migration batch declares first and
loads second; the subject and object projections of the predicate category are
implicit in `query_cells`, not first-class morphisms.

## The graph

Everything is a cell ⟨subject, predicate, object⟩ with a value in {⊥, t, f, ⊤}.
Entities are subjects with an `is-a` cell at t; ids look like `kind:slug`
(act kinds carry their subject and a time fragment, e.g. `attempt:store-…`).
Predicates carry domain, range, functionality, acyclicity, and optionally the
predicate they specialize or invert (`ontology` tool, `/ontology`, where kinds
and predicates are also declared). Kinds form a tree under `extends`; a
declared kind's id names it (`kind:customer` declares `customer`, whose
instances are `customer:acme`). Transactions are entities too: a justification
is a cell on the transaction that carried the revision. Crosslinks for
migrated records: `provenance` (the source path or utterance), `same-as` (an
external identifier: URI, NI, path, ticket), `supersedes` (the record this one
replaces), `related-to`.

Derived, never stored: status, readiness, blockers, horizon, modality, work
type, concordance, settlement nuclei, strata, regime and closure ordinal,
milestone reached, progress, cost, estimate, budget fit, bottleneck, failure
kind, capability propagation, dispatch fit and restrictions, learning rate,
deontic compliance and operativity, front, ordinal stage, causation, merge
anomalies, self-description drift.

## What phase 4 settled

Each line is a property the suite states as a law (`test/laws.test.mjs`,
`docs/settled-architecture-phase-4.md` §4).

- **Two identities.** A transaction names evidence (wall time inside the
  digest); a message names intent (wall time excluded). Replay is decided by a
  derived `msg → tx` index, never by weakening the evidence digest.
- **One refusal shape.** Every refused call, through every door, is
  `{refused, code, errors, warnings, evidence?}` with a code from a closed set;
  no bare `{error}` and no unhandled exception escapes `runTool`.
- **One entry point.** Every door decodes its wire shape to
  `{tool, arguments, correlation}` and dispatches through `runTool`; a door
  never computes a reading itself. Each tool row declares an `inputSchema`, an
  `outputSchema` and an `effect`, and `READ_ONLY_TOOLS` is derived from the
  effect rather than kept in parallel.
- **Strata, checked over the source text.** Admission is the only stratum that
  appends, reads the clock, or mints an id; the derivations below it do none of
  those, and the test slices the file between the banners to say so.
- **Time and randomness are injected.** `Engine` and `Capabilities` take a
  `{clock, ids}` pair, so two engines over the same fresh log with a fixed clock
  and id source append byte-identical transactions.
- **The engine describes itself.** `describe_self` materializes one operation
  symbol per tool (slots, `yields`, `effect`, `branching`) and the package,
  engine, service and resource cells (`version`, `located-at`, `exports`,
  `interface`, `holds-state-in`) — never a count, a status, or any other derived
  reading — and a second run with nothing changed appends nothing. `self` and
  `/about` answer live from the tool table and the filesystem;
  `check().selfDescriptionDrift` reports every recorded cell that no longer
  matches what the code and the files say.
- **Honest categorical names.** `kind_category` reports `initial` / `terminal`
  over the whole morphism set (empty, which is the true answer) and the
  in/out-degree-zero kinds of the containment subgraph under their own names,
  `containment.sources` and `containment.sinks`.

## Doors

| Door | Where |
| --- | --- |
| CLI | `call <tool> [json]`, `check`, `export`, `schema [kind]`, `merge <log>`, `mint`, `caps`, `revoke-cap` |
| MCP stdio | `node planning-engine.mjs mcp` (tools, resources `planning://…`, versions 2025-06-18 / 2025-03-26 / 2024-11-05, no batching) |
| MCP streamable HTTP | `POST /mcp` |
| OpenAPI 3.1 | `GET /openapi.json`; every tool is `POST /api/call/{tool}`; read-only tools also `GET /api/call/{tool}?arg=value` |
| JSON / JSON-LD / JSON Schema | `GET /api/entity/{id}` (Accept `application/ld+json` or `?format=jsonld`), `GET /context.jsonld`, `GET /api/schema[/{kind}]` |
| NDJSON-LD | `GET /export.ndjson`, `POST /import.ndjson` |
| CloudEvents 1.0 | `GET /events?since=N`, `POST /events` with data `{tool, arguments}`, `GET /events/stream` (SSE) |
| ActivityStreams 2.0 | `GET /outbox`, `GET /activities/{tx}`, `GET /actors/{id}`, `POST /inbox` (Create, Update, Delete, Add, Remove, Accept, Invoke) |
| A2A | `GET /.well-known/agent.json`, `POST /a2a` (`message/send` with a data part `{tool, arguments}`) |
| HTML | `/`, `/roadmap`, `/roadmap/{id}`, `/kinds/{kind}`, `/entity/{id}` (with a create-and-attach form for components), `/frontier/{id}`, `/readout/{id}`, `/next`, `/query`, `/log`, `/deontic`, `/ontology` (declare kinds and predicates), `/check`, `/doors`, `/about` |

Tools added in 0.3: `roadmap`, `create_batch` (up to 500 entities in one
transaction, admitted whole or refused whole, later entries may reference
earlier ones), `declare_kind`, `declare_predicate`, `resource_graph`, `term`.
Phase 4 adds `self` (what this engine is, computed live) and `describe_self`
(the same description materialized into the log).

## What work takes, what it changes, who does it

The theory of work (Corollary 4.1) says a work-act is a transition on state
bundles, equivalently a Petri transition or a Reiter action: input places it
requires, output places it produces, a cost, and a capability that updates. The
graph is the state, so the engine says this in cells:

| On the operation (patterns; `$slot` binds through the work's `parameter`s, `$self` is the work) | On the work itself (concrete cells) | Read as |
| --- | --- | --- |
| `requires "s p o"` | `precondition "s p o"` | what it takes: cells that must be at t before the work is ready (enabledness). `unmet` lists the ones that are not. |
| `produces "s p o"` | `postcondition "s p o"` | what it changes to t on completion. These are the work's goal cells (T = (G_T, S_T, v₀)). |
| `consumes "s p o"` | `undoes "s p o"` | what it changes to f on completion. Everything not named is unchanged: the frame axiom. |

`signature {id}` returns the instantiated preconditions with their current
values, the effects and undoings, the resources touched, and open `$slot`s.
Readiness is dependency order **and** enabledness. Completion (a success
attempt or `attest completed`) witnesses the becoming on the resources: effects
to t, undoings to f. Completion is not witnessed while an effect cell is not at
t. `resource_graph` shows which open work changes a resource (`changedBy`) and
which waits on it (`neededBy`); `check` reports `contention`: open work that
writes the same cell.

The theory of governance gives who: an office is a position type; its
incumbents are tokens; the office holds Hohfeldian positions over operations:
`has-duty`, `has-power`, `has-liberty`, `has-immunity`. Work applying an
operation is **accountable** to the offices with duty or power over it, or to a
declared `responsible-office` found up the plan. Delegation moves authority and
never accountability: a dispatcher who is not an incumbent of an accountable
office must hold authority traced to it (`has-authority office:x` or
`office:x:<scope>`), else `NOT_ACCOUNTABLE`. `whoOf` on every task reading and
brief entry gives the accountable offices with incumbents, who holds the work,
who dispatched it, and the norms naming it; `check` lists `unattendedDuties`:
offices with a duty over an operation whose open work nobody holds.

## The brakes

The engine refuses the work nobody asked for. Four gates, all read off cells a
governing party writes:

| Gate | Refusal | What lifts it |
| --- | --- | --- |
| **Actor binding.** A process started with `PLANNING_ENGINE_ACTOR` writes only as that actor. `.mcp.json` binds Claude's server to `worker:claude`, the Codex harness binds `worker:codex`, the systemd service binds the owner. | `IMPERSONATION` | `has-authority act-as:<id>` granted to the bound actor. |
| **Commitment.** Nothing under an endeavor, campaign, project, or plan can be dispatched or claimed until a container above it carries `committed-by` from a holder of `planning-engine:govern` (or a collective). | `UNCOMMITTED` | `commit_to {id, by, budget}` by a governing party. |
| **Budget.** The nearest `budget` in the lineage is a ceiling over recorded attempt costs plus the estimates of open and held work. No budget above the work, or not enough left, refuses dispatch. `spend` is on the brief. | `OVER_BUDGET` | The governing party sets or raises the budget, abandons work, or the estimates come down. |
| **Hold.** A governing party's `hold {id, reason}` is the owner's "later": nothing under it starts. | `ON_HOLD` | `unlink` the hold cell with a justification. |

`committed-by`, `budget`, `hold`, and `has-authority` are governing cells: once
any party holds `planning-engine:govern`, only such a party can write them.
Until then the ledger is open, so a fresh log bootstraps without ceremony.

Every task on the brief carries its `brakes`, so an agent sees before it acts
which gate would stop it and who can lift it. `check` lists the governors and
any held work that no longer passes the gates.

## Authority

HTTP writes are object capabilities. With no token minted the local server is
open. Once a token exists, writes need `Authorization: Bearer <token>` (or
`?cap=<token>` once for the forms, which sets a cookie; prefer the header for
anything beyond casual local use). A token names an actor, a tool scope, and
optionally a container; `--parent` mints an attenuation that can only narrow.
Every write tool declares which argument its scope is checked against; tools
that create unscoped state (`found`) are refused under a scoped token, and a
scoped `create_entity` must anchor the new entity inside the scope. Reads never
need a token. Every transaction's actor must be an existing worker, collective,
or office. The capability file is re-read when it changes, so minting takes
effect without a restart.

## Agents

The agent's door is six tools, sized to be read in one call:

| Tool | What it gives an agent |
| --- | --- |
| `brief {worker, limit}` | Focus and its readout; the norms binding the worker and its restrictions; what it holds (goal, blockers, open saturation slots, `verified-by`); ready work under its focus; the last session's handoff; what changed since; how to close work. Long text is clipped, lists capped. Call it first. |
| `session_open {worker, focus?}` / `session_close {cycle, by, summary, produced}` | A session is a cycle of the operations loop. Opening witnesses planning and returns the brief; closing witnesses the other five phases in order, stores the summary as the handoff the next brief shows, and observes the focus. |
| `claim {task, by}` | Take ready work yourself: a self-dispatch under the standing authority `self-claim` (granted once with `has-authority` on the worker, its office, or its collective). Refused with `HELD` when someone else holds it. |
| `changes {since, limit}` | One compact row per transaction since a stage. |
| `search {q, kind, limit}` | Substring search over id, title, description before creating anything. `create_entity` also warns when a same-titled entity of the kind exists. |
| `record_event {task, by, checkCommand, exitStatus}` | Verification as a real command and its real exit status. A task with `verified-by` refuses completion (`EVIDENCE_REQUIRED`) until an event carries that command with exit status 0. |

`create_entity` takes `in` to attach the new entity to its container in the same
transaction, so nothing is created orphaned. `next_work` with a `worker` hides
tasks held by another worker and ranks work under any worker's focus first at
equal horizon. The roadmap's horizon bands are capped (`limit`, default 12) with
exact `counts`, focus-ranked, and joined by an `attention` list of ready work.

Durability: the log is ignored by git. Every 25 transactions a snapshot is kept
beside it (`data/snapshots/`, last five). A process that finds its log shorter
than what it already folded rewrites the file from memory and re-admits any
stray lines instead of resetting; a fresh open that finds the live file behind
the newest snapshot restores from it (`node planning-engine.mjs recover` does
the same by hand). `check` reports `healed`, `recovered`, and the snapshot.

The CLI takes arguments inline, from a file (`call create_batch @batch.json`),
or from stdin (`call create_batch -`). Kinds and predicates declared in a batch
are usable by the entities that follow them in the same batch.

## Migrating the existing planning knowledge

An inventory of the tree found planning knowledge in eleven forms. The ones
that matter, and how each lands here:

| Form in the tree | Lands as |
| --- | --- |
| Goal-stack roadmap cuts (`…enterprise-project-management…/data/records/*-goal-stack-roadmap.json`, prose `shipped[]` / `nextEdges[]` / `brokenEdge`, chained by `extends`) | One endeavor per thread; each `nextEdges` sentence a task with `provenance` = the cut's path; `shipped` items as tasks attested completed; `carriers[]` as `provenance`; later cuts `supersedes` earlier ones. Their `state` prose is dropped: status is derived here. |
| Campaign / milestone / task markdown with frontmatter (`docs/dev/{campaigns,milestones,tasks,goals,backlog}/*.md`, mostly under `lib/legacy`) | campaign, milestone (`target-by-ord` → `target-date`), task (`depends-on-tasks` → `depends-on`, `estimated-effort-hours` → `estimated-cost`, `deadline-by-ord` → `deadline`, `folds-into` → `supersedes`, `owned-by-office` → dispatch, `of-*` → `contains`). Stored `horizon`, `status`, `completion-percent` are refused at the door: derived or nothing. |
| Agency pools (`lib/agency/{offices,duties,works,incumbencies}/*.json`, about sixty pools) | office with `deontic-profile`, `has-authority`, `seats`; each duty a MUST norm with `correlative`, `receiver-condition`, `allowed-effect`, `requires-capability`, `delegable`; `x-provenance.migrated-from` → `provenance`; incumbencies → `holds-office`. |
| Work orders (`work-orders/wo-*.json`, demand + evidence + commit) | task with `provenance`; the realization an attempt with `produced` = the commit and result digest (`same-as` for the sha256). |
| Rulings (`…/data/records/*-ruling-*.json`) | norms attributed to the founding collective with `provenance` = the record path. |
| Program carriers (README + business plan + capability spec) | enterprise or endeavor with charter and goal; bootstrap rungs as projects; nothing dated or stateful copied. |
| Work-state readout schema and the EAVT rail (`work-state-readout.schema.json`, `witness-journal-seavt.jsonl`) | Already engine-shaped: intents → tasks, allocations → assignments, frontier and completions derived, `record.<sha256>` → `same-as`. |

Phases, each gated by the roadmap's coherence findings going to zero for what
that phase admitted:

1. **Declare.** `declare_kind` / `declare_predicate` for what the core lacks
   (customer, employee, dataset, product, program…; `deploys specializes
   acts-on` and the like). One batch, committed, reviewed on `/ontology`.
2. **Parties and resources.** Offices, workers, collectives, packages,
   services, engines from the agency pools and the package tree, with
   `provenance` and `same-as`; incumbencies and `part-of`.
3. **Endeavors and campaigns.** Programs and roadmap-cut threads as
   endeavors and campaigns with charters, goals, objectives, and milestones;
   cuts chained by `supersedes`.
4. **Tasks.** Each source form's task records under their containers with
   `depends-on`, roles (`acts-on`, `uses`, `for-party`), estimates, deadlines.
   Path references resolve to ids through `same-as`; unresolved ones stay as
   `provenance` and surface as coherence findings.
5. **Duties and norms.** Agency duties and rulings as norms with their
   correlatives and receiver conditions; `deontic_readings` then reads
   compliance off the same cells the tasks live in.
6. **Retire the sources.** Only when the derived roadmap reproduces what each
   handwritten record said; the record's path stays as `provenance`.

`create_batch` is the door for every phase; `/import.ndjson` takes JSON-LD
nodes for tooling that already speaks it.

## Verification

`npm test` is `node --test test/*.test.mjs`: **every** suite under `test/`, 60
tests. The suites are the original behaviors (`planning-engine.test.mjs`, 15);
one test per reviewed finding (`review-findings.test.mjs`, 17 — scope escape,
supersession race, torn tail, a 2,000-task chain under a time budget, claiming,
propagation, seats and focus, budgets and learning rate, nuclei and closure
ordinal, governance becoming and restrictions, workflow patterns, capability
file sync, MCP negotiation, schema tools, merge, and the HTTP doors); the
resource-graph suite (`resource-graph.test.mjs`, 5 — declared kinds with
subsumption, inherited requirements, schema and category inclusions, retire
guards; declared predicates as families within their parent, converses,
conformance reporting; work as terms; atomic batches and scoped refusal of
declarations; the derived roadmap with saturation slots, milestone and dated
drift, cross-lane coupling, and coherence findings, rendered over HTTP); and
the law suite (`laws.test.mjs`, 23 — the property statements of
`docs/settled-architecture-phase-4.md` §4: the repair fold and merge as a
lattice join, merge anomalies, cost under a diamond dependency, byte-identical
admission under a fixed clock, the one refusal shape at every door, the schema
validator, every tool's result against its declared `outputSchema`, no door
past `runTool`, effect-free derivations, the two nuclei disagreeing, initial
and terminal over all morphisms, `BOUNDARY_TYPE` on mismatched workflow
nesting, message replay and tamper detection, atomic review admission,
correlation through every codec, `describe_self` twice, self-description drift,
and L16: the version `package.json` declares equals `VERSION` and the test
script runs every suite).

The counts above are the ones the command reports; `self` (or `/about`) reads
them off the suites on disk, and `check().selfDescriptionDrift` reports any
count written into the log that has gone stale.
