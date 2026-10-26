# SPOTCOMP Experimental Derivation Profile

Status: draft, not yet complete enough for a final normative implementation.

This document states the current best experimental profile.
It must be read with [RESEARCH-LEDGER.md](./RESEARCH-LEDGER.md) and [DERIVATION-OBLIGATIONS.md](./DERIVATION-OBLIGATIONS.md): open derivation obligations block final conformance claims.
Implementations in `src/` are probes, not authorities for this profile.

SPOTCOMP is read in this workspace as Subject-Predicate-Object Trace Computer Operating Modeled-Players.
The profile is therefore incomplete unless it derives all of those positions: subject/predicate/object predication, trace, computer substrate, operating mode, modeled players, and the concurrent-game/ludic structures that make modeled players mathematically meaningful.

The key words MUST, MUST NOT, SHOULD, SHOULD NOT, MAY, and OPTIONAL in this document are to be interpreted as described in RFC 2119 and RFC 8174 when, and only when, they appear in all capitals.

## 1. Scope

This profile specifies the current candidate shape of a SPOTCOMP swarm:

1. The trace substrate.
2. The directory and category discipline.
3. The finite projection and settlement interface.
4. Modeled-player participation.
5. Federation and IETF conformance.

This profile intentionally does not make FOUR the global substrate.
FOUR MAY be used as a finite fiber algebra for a settlement or projection, but implementations MUST NOT require every EAVT value to be a FOUR value.

## 2. Core Objects

### 2.1 EAVT Trace Row

An EAVT row is a JSON object with exactly these top-level members:

- `e`: entity, the subject or resource being traced.
- `a`: attribute, predicate, morphism, or generator being applied/read.
- `v`: value, any JSON value.
- `t`: transaction time or transaction identifier.

An implementation MUST treat an append-only sequence of EAVT rows as the trace object.
It MUST NOT treat the trace as a wrapper around a special value algebra.

The `v` member MAY contain a scalar, object, array, URI string, content hash, or finite algebra element.
A row whose `v` is `true` is a boolean-true finite projection row, not a different kind of row.

When `v` carries a predication value, the implementation MUST declare the active fiber context.
The general predication fiber is `A_p = (L x L)^(E x E)` for declared lattice `L`, predicate category, and entity set `E`.
FOUR values MAY appear only under a declared boolean specialization or finite projection boundary.

### 2.2 JSONL Trace File

A JSONL trace file is a UTF-8 text file containing one EAVT JSON object per line.
Blank lines SHOULD be rejected in canonical trace files.
Non-canonical importers MAY ignore blank lines before canonicalizing.

Line order is presentation order.
Trace identity for merge MUST be based on canonical row identity, not byte position.

Canonical row identity is `sha256(jcs(row))`, where `jcs(row)` is the RFC 8785 canonical JSON serialization of the exact EAVT row under the RFC 7493/I-JSON preconditions required by JCS.
Implementations MUST reject or quarantine rows that cannot be proven duplicate-name-free, valid-Unicode, finite-number JSON inputs.
[CANONICAL-IDENTITY.md](./CANONICAL-IDENTITY.md) gives the candidate checker profile for row IDs, signed envelope bytes, stream item identity, and timestamp policy.

### 2.3 Trace Order

Let `Trace` be the set of finite EAVT row sets, ordered by inclusion.
Appending a row is monotone.
Directed joins are unions.
Implementations MUST preserve append-only monotonicity: prior rows are not edited to change truth, status, or settlement.

### 2.4 Projection

A projection is a deterministic, monotone function from an EAVT trace to a finite artifact or finite algebra.

Examples:

- SHP projection: rows settled for a semantic hypertext view become a finite Semantic Hypertext Packet.
- FOUR projection: rows in a selected fiber are projected to a finite four-cornered settlement.
- Index projection: rows about paths, aliases, and schemas become an implementation index.

Implementations MUST record enough source rows for a projection to be reproducible.
A projection artifact SHOULD include or reference the trace frontier it was projected from.

Semantic hypertext projections use [SHP.md](./SHP.md).

Recognition is a trace-axis and admission discipline, not parse success or row presence.
Implementations MUST NOT treat a syntactically valid row, a successful shape check, or an authenticated envelope as admitted evidence until the relevant recognition, canonical identity, governance, observation, action, and capability gates have been satisfied.
[RECOGNITION.md](./RECOGNITION.md) gives the current declaration profile for this boundary.

## 3. Directory Discipline

SPOTCOMP directory structure is categorical, not object-oriented.

For a category rooted at `$thing`:

- `library/$object/` names codomain objects produced by generators of `$thing`.
- `$thing/$morphism/` names a generator, transformer, or morphism available from the category root.
- `scripts/` under a morphism contains executable witnesses of that morphism.
- `*.schema.json` is the finite type/proposition witness for a resource.
- `*.jsonl` is the trace at that path.
- SHP artifacts are finite semantic hypertext projections of relevant trace frontiers.

An implementation MUST be able to classify each directory node it manages as one of:

- category root,
- generator/morphism,
- codomain object,
- projection artifact,
- implementation support.

For each generator, the implementation MUST record whether the generator extends its input category, restricts it, or is admitted as a scoped coincidence theorem between distinct morphism positions.
Extension generators MUST cite an embedding witness or open obligation and name the structure they add.
Restriction generators MUST cite the source frontier, subobject, or larger category being restricted and name the axes or coordinates forgotten by the codomain claim.
Coincidence declarations MUST cite theorem name, scope, and off-scope distinctness.
Unknown variance is development metadata only and MUST NOT be treated as strong conformance evidence.

[PATH-TYPING.md](./PATH-TYPING.md) gives the candidate checker profile for this discipline, including path roles, TRC schema/log/script co-location, dual filing, and rejection cases.

[GENERATOR-VARIANCE.md](./GENERATOR-VARIANCE.md) refines the variance obligation into a declaration profile for extension, restriction, and coincidence criteria.

## 4. Foundational Pipeline

The foundational pipeline is:

`articulating -> predicating -> positing -> settling`

This direction is normative.
Implementations MUST NOT make downstream finite settlement rules prerequisites for upstream articulation.

- Articulating generates the aperiodic predication category: it brings a potential cell or position into being.
- Predicating generates the transfinite predication category: it opens the predication-category around a Frege-saturated position.
- Positing generates the Scott-continuous predication category: it performs knowledge-order least extension, with EAVT rows as finite event presentations.
- Settling generates the finite predication category: it projects a monotone trajectory frontier into a finite, checkable algebra or artifact.

FOUR belongs at or below settling as one finite algebra.
It is not the substrate of positing.

[PREDICATION-STAGES.md](./PREDICATION-STAGES.md) gives the candidate checker profile for this stage/category distinction.

[PRELOCUTIONARY-INGRESS.md](./PRELOCUTIONARY-INGRESS.md) adds the ingress boundary before locution: external trigger bytes are not trace evidence, token/claim/utterance ground articulating, and script, hook, or HTTP handlers must preserve stage declarations before any illocutionary event is emitted.

[PREDICATION-FIBER-ALGEBRA.md](./PREDICATION-FIBER-ALGEBRA.md) gives the candidate checker profile for the value substrate: pointwise bilattice/residuated fibers, fibration reindexing, hyperdoctrine properties, and the rule that non-FOUR fibers remain legal whenever `L` is not boolean.

[POSITING.md](./POSITING.md) refines this point: categorical positing is the knowledge-order least-extension morphism, while exact EAVT rows are finite event presentations.
Implementations MUST keep locutionary decoding, pure illocutionary event formation, and perlocutionary writes/closure propagation distinct in their conformance evidence.

[CHL-LANGUAGE-CONES.md](./CHL-LANGUAGE-CONES.md) records the CHL language-cone boundary.
Implementations MUST NOT collapse articulating, predicating, positing, settling, proof, term-instantiation, existential push-forward, path-resolving, and SHP projection into one generic operation unless they cite the exact coincidence theorem and its scope.

## 5. Trace Operations

### 5.1 Append

Append takes an EAVT row and a trace and returns a trace containing that row.
Append MUST be inflationary and idempotent with respect to canonical row identity.

### 5.2 Merge

Merge takes two traces and returns their canonical union.
Merge MUST be commutative, associative, and idempotent.
A conforming merge is therefore a state-based CRDT merge over finite EAVT row sets.

### 5.3 Settle

Settle takes a trace frontier, a finite projection rule set, and a target finite algebra.
It returns a finite settlement artifact and the frontier identity.

Settle MUST be deterministic for a fixed trace frontier, rule set, and target algebra.
If a rule set is not monotone over trace inclusion, it MUST NOT be advertised as a SPOTCOMP settlement rule set.

A final settlement claim MUST cite the closure-rule system, source frontier or increment sequence, regime or closure ordinal claim, and evidence that the emitted state is closure-fixed.
Bounded rule execution without such evidence is only a partial prefix.
[CLOSURE-SETTLING.md](./CLOSURE-SETTLING.md) gives the current closure 2-monad, settling endofunctor, and sigma/delta declaration surface.

## 6. Modeled Players And Swarms

A modeled player is a participant whose actions are represented by EAVT traces and whose interaction capacity is modeled as a strategy in a concurrent game system.

A conforming swarm implementation MUST represent each modeled player with:

- stable player identifier,
- external-player reference distinct from the system-held modeled-player record,
- identity key or authenticated local authority,
- readable capability set,
- writable action surface,
- observation bounds,
- governance regime,
- trace inbox,
- trace outbox.
- local-settling reference;
- CGS strategy/profile reference.

The trace inbox and trace outbox are EAVT JSONL traces.
Transport envelopes MAY wrap batches of rows, but the payload semantics are EAVT trace semantics.

If the modeled player is character-kind, the implementation MUST also bind the player to a character record and keep persona, role, skill, method/tool surface, teaching, installation, and player-binding positions distinct.
A key, inbox, and outbox are not sufficient modeled-player evidence.

See [MODELED-PLAYERS.md](./MODELED-PLAYERS.md) and [PLAYER-CHARACTER-BOUNDARY.md](./PLAYER-CHARACTER-BOUNDARY.md) for the mathematical layer.

Structural swarm roles such as leader, validator, observer, or actor MUST be derived from recognition cells and governance.
Implementations MUST NOT infer such roles from out-of-band flags alone.
Unknown recognition blocks strong swarm conformance.

Modeled-player strategy equivalence MUST be CGS-shaped.
Key identity, trace-loop equality, or identical handler code is not enough.
A strong swarm profile must expose the concurrent-strategy law surface recorded in [CGS-STRATEGY-LAWS.md](./CGS-STRATEGY-LAWS.md), including receptivity, symmetry quotienting, interaction-and-hiding composition, and any declared sequential/innocent restrictions.

Continuous learning MUST be represented as governed change in the modeled player's settling, skill surface, memory fragment, or closure-rule system.
Answering, referencing, teaching, skill improvement, and rule learning MUST remain distinguishable.
Hidden runtime adaptation, context presence, or host installation alone is not learning evidence.

## 7. Federation

Federation moves EAVT trace rows between modeled players or SPOTCOMP instances.

A federated sender MUST sign the canonical payload.
A receiver MUST verify the signature before ingesting rows into its local trace.
Invalid signatures MUST be rejected and MAY be recorded as local denial or audit rows.

Signature verification is necessary but not sufficient for local admission.
Receivers MUST apply canonical identity, recognition, and governance gates before merging rows into an admitted frontier.

Federated ingestion MUST be merge-based.
It MUST NOT depend on synchronized clocks, total message order, or destructive overwrite.

The current experimental envelope shape is specified in [schema/envelope.schema.json](./schema/envelope.schema.json).
Implementations MAY use a different transport envelope only if the signed payload still has EAVT trace semantics and satisfies [IETF-CONFORMANCE.md](./IETF-CONFORMANCE.md).

Envelope signatures MUST cover JCS canonical bytes of the unsigned envelope.
JSON text sequences used for streaming do not have sequence-level canonical JSON identity; signed streams MUST sign item canonical bytes or a manifest of canonical row IDs.

Federation profiles MUST be regime-aware.
Endpoint-state payloads are not interchangeable with trajectory or trace-increment payloads.
[REGIME-FEDERATION.md](./REGIME-FEDERATION.md) defines the candidate compatibility rules for strict, Scott-continuous, transfinite-bounded, and aperiodic regimes.

## 8. Candidate Conformance Classes

These classes are provisional.
They are useful for staged implementation work, but final SPOTCOMP conformance additionally depends on the open derivations in [DERIVATION-OBLIGATIONS.md](./DERIVATION-OBLIGATIONS.md).

### 8.1 Trace-Conformant Implementation

An implementation is trace-conformant if it:

- reads and writes canonical EAVT JSONL traces,
- validates row shape,
- canonicalizes row identity,
- performs append and merge monotonically,
- can replay a trace from an empty state.

### 8.2 Settlement-Conformant Implementation

An implementation is settlement-conformant if it is trace-conformant and:

- declares finite projection rule sets,
- checks monotonicity obligations for those rules or marks them unproved,
- emits reproducible finite artifacts with frontier identity.

### 8.3 Swarm-Conformant Implementation

An implementation is swarm-conformant if it is settlement-conformant and:

- models players with inbox/outbox traces,
- authenticates federated trace batches,
- supports merge-based federation,
- records capability, observation, and action bounds.
