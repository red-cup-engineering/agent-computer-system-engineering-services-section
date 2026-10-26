# Implementation Probe

Status: non-normative probe.

This guide describes a small implementation probe for candidate trace and federation laws.
It is not a claim that the code in this directory is SPOTCOMP-conformant.
The consolidated implementable core is [library/implementation/specification.md](./library/implementation/specification.md); this file remains a probe inventory for the current `src/` code.

For the basic function surface over JSONL EAVT SPOTs, the subject-predicate-object cell traces, see [NORMATIVE-FUNCTIONS.md](./NORMATIVE-FUNCTIONS.md).
For their implementation laws, see [FUNCTION-LAWS.md](./FUNCTION-LAWS.md).
For the operational mathematical function contracts behind those functions, see [OPERATIONAL-MATH-FUNCTIONS.md](./OPERATIONAL-MATH-FUNCTIONS.md).

For the compact row/log/packet/wire/admission rulebook, see [TRACE-PACKET-TRANSPORT.md](./TRACE-PACKET-TRANSPORT.md).
For the function-composition contract for swarms, see [SWARM-FUNCTIONS.md](./SWARM-FUNCTIONS.md).

Do not bend the specification toward `src/`.
Change or discard the probe when the repo-derived categorical invariants require it.

## 1. Candidate Runtime Components

A future SPOTCOMP swarm runtime is expected to need at least:

- PAM kernel: Predicate Algebra Modeling over declared entity, predicate, value, fiber, morphism, reification, settlement, replay, and witness surfaces.
- TRC/TDP runtime: the on-disk typed resource catalog as the running theory derivation program, with schemas, logs, morphism scripts, dual filing, replay, and closure execution treated as one proof-tree surface.
- Operations declaration and record checkers: record processes, procedures, work types, ledgers, budgets, Lawvere-quantale costs, operations-loop events, and stationarity/Laplacian evidence before host activity is treated as SPOTCOMP operating behavior.
- CGS runtime/profile layer: records prime-event-structure arenas, polarity, causality, conflict, symmetry, concurrent strategy morphism declarations, receptivity evidence, and interaction-and-hiding composition witnesses before player behavior is treated as game-semantic evidence.
- Modeled-player runtime/profile layer: records external/model/player boundaries, ruled observer-local settlings, handedness, player-local observation, CGS strategy handoff, aperiodic swarm witness references, and governed learning transitions before peer records are treated as modeled players.
- Trace store: append-only EAVT JSONL files plus canonical row IDs.
- Canonical identity checker: records JCS/I-JSON preconditions, duplicate-name parse evidence, row ID formula, envelope signature bytes, stream item identity, and timestamp policy before wire evidence is trusted.
- Trace-monoid settlement checker: records finite step set, independence relation, valuation action, Foata/prefix evidence, and closure-driven CRDT convergence scope before order-independent settlement is treated as evidence.
- Predication-stage declaration checker: records articulating/predicating/positing/settling as aperiodic/transfinite/Scott-continuous/finite predication categories before locution or row-level probes are treated as evidence.
- Prelocutionary ingress checker: records token/claim/utterance grounding and script, hook, or HTTP handler declarations before external trigger bytes are treated as typed internal input.
- I/O articulation checker: records external I/O, LLM prompts/completions, hidden context, tool calls, unresolved inputs, and standards bindings as articulation-boundary declarations before they are treated as trace, witness, or settlement evidence.
- Proof-tree irresolution checker: records recursion grounding, stage preservation, partial-map/default discipline, fixed-point versus prefix boundaries, TRC/TDP replay, outside-system limits, and standards placement before unresolved behavior is treated as a result.
- Predication-fiber declaration checker: records declared `L`, predicate category, `E`, `A_p = (L x L)^(E x E)`, fibration axioms, hyperdoctrine properties, and FOUR-specialization boundaries before value checks are treated as evidence.
- Closure/settling apex declaration checker: records closure 2-monad axioms, settling endofunctor shape, apex evidence, sigma/delta cycle, and bounded-fuel partiality before a runtime claims final settlement.
- CHL language-cone declaration checker: records the language apex, column legs, distinct morphism positions, scoped coincidence, path-theory column, and command-composition boundary before a compact runtime command is treated as evidence.
- Generator-variance declaration checker: records extension embeddings, restriction frontiers, coincidence scopes, and unknown-variance downgrades before a generator is treated as layout evidence.
- Trace-axis declaration checker: records the rich trace axes and projection-forgetting boundary before row-level probes are treated as evidence.
- Recognition declaration checker: records recognition as trace axis, receiver-relative admission, and role-recognition discipline before row presence, parse success, or shape checks are treated as admitted evidence.
- Positing boundary checker: records the Scott-continuous positing morphism, naturality surface, and locution/illocution/perlocution split before row-writing code is treated as evidence.
- Projection engine: deterministic finite projections from a trace frontier.
- Settlement engine: monotone finite rule iteration when the projection target is an algebra.
- Player registry: modeled-player records with identity keys, capabilities, handedness, inboxes, and outboxes.
- Player/character boundary checker: rejects key/inbox/outbox-only player evidence and requires external/model distinction, local settling, character/persona/role/skill bindings when applicable, governance, handedness, and CGS strategy references.
- CGS strategy-law declaration checker: records morphism-level concurrent strategy obligations before player loops or policy tables are treated as strategy equivalence evidence.
- Bigraded diamond swarm declaration checker: records closure KZ/fibration KZ axes, truth/knowledge common-knowledge separation, bigraded cohomology, multi-observer swarms, aperiodic tiling witnesses, and the DRIP/Remote ID boundary before a swarm is treated as strongly modeled-player conformant.
- Aperiodic swarm witness checker: records local-settling tiles, substitution/direct-limit/MLD evidence, classifying invariant slots, bilattice-alignment commutation, and weighted-stability downgrade rules before a swarm uses aperiodic tiling language as evidence.
- Modeled-player swarm dynamics checker: records the external-player/model/character boundary, ruled observer-local settlings, agentive positing, network-sheaf consensus, CGS strategy preconditions, transition dynamics, and aperiodic witness boundary before player records are treated as mathematically modeled players.
- Continuous-learning declaration checker: records answering/referencing, teaching, skill closure, memory-local-fragment, rule-learning transition, and ludic/CGS admissibility boundaries before runtime adaptation is treated as modeled-player learning evidence.
- Moduli/descent/Laplacian declaration checker: records meta-moduli descent, rule-system closure-equivalence, settling-vs-meta regime stratification, regime-sensitive named substitutions, Q-enriched Laplacian cohomology scope, Verdier/six-functor scope, and strong-MLD firing-orbit data before a swarm upgrades ordinary MLD into strong conformance.
- Regime substitution ladder checker: records Padovan finite/strict placement, Fibonacci Scott-continuous placement, Tribonacci transfinite placement, benchmark-lift separation, step-n moduli coordinates, and bilattice alignment boundaries before substitution examples are used as regime evidence.
- Realizability/deformation declaration checker: records the meta-realizability map, increment-sequence fibers, realizability axes, predicate-naturality coupling, tangent-dimension non-semicontinuity, and CHL-stabilization scope before a swarm claims a realized class or terminal classifier.
- Void relationlessness declaration checker: records old void-cone vocabulary as four-stage predication machinery, void as the null relationless case, associated-graded/apex pairing, value-agnostic null instances, and weighted rank-collapse boundaries before a swarm uses void or failure-geometry claims as evidence.
- DRIP/UAS binding checker: records DET/UAS ID, broadcast RID authentication, DNS/DIME registry lookup, and standards-layer admission boundaries before a UAS deployment claims DRIP conformance.
- Federation admission gate: verifies signed envelopes and records canonical identity, local recognition, governance, capability, player-local bounds, regime binding, and outcome before merge.
- Governance gate: restricts side-effecting actions through modal authorization/capability evidence before effects commit.
- SHP producer: emits finite semantic hypertext packets from trace frontiers.
- Cohomology audit surface: records regime-sensitive `H1_t`/`H1_top` claims, inconsistency top-cell witnesses, and downgrade policy for unverifiable claims.

## 2. Trace Store

The trace store MUST reject rows that are not exactly `e`, `a`, `v`, and `t` JSON objects.
It SHOULD keep a row-ID index using:

`sha256(RFC8785-JCS(row))`

Rows are immutable.
Corrections, denials, withdrawals, and replacements are new rows.

## 3. Federation Ingestion

Ingress algorithm:

1. Parse the envelope as JSON.
2. Check `profile == "spotcomp-eavt-envelope-v1"`.
3. Resolve `sender` and `keyId` to an authorized Ed25519 public key.
4. Verify the signature over the canonical unsigned envelope.
5. Validate each EAVT row.
6. Check the sender and row set against the governance projection for the relevant authorization frontier.
7. Merge admitted rows by canonical row identity.
8. Record rejections as local audit EAVT rows.

Signature verification happens before merge.
Governance can reject a validly signed row set, but it does not make signature verification optional.

## 4. Player Loop

A modeled player loop is:

1. Read an observable frontier from the inbox and any permitted shared traces.
2. Project the observable frontier into the player's working view.
3. Apply the player's strategy under its handedness and governance bounds.
4. Append resulting EAVT rows to the outbox.
5. Optionally sign an envelope for federation.

Players MUST NOT require a global synchronized frontier.
Different players may act from different partial observations.

## 5. SHP Projection

An SHP projection takes:

- trace frontier,
- projection rule set,
- target entity or packet identifier,
- producer modeled-player identifier.

It emits a finite HTML packet without scripts or required external dependencies.
Each packet element should carry structural classes and source-coordinate metadata sufficient to audit the projection against the trace.
RFC-shaped packets should satisfy the RFC 7992 inhabitant constraints recorded in [SHP.md](./SHP.md).

## 6. Demonstrator Code

The code in `src/` is a law probe, not a standards-complete implementation:

- [src/trace.mjs](./src/trace.mjs) validates EAVT rows, computes canonical row IDs, merges traces, and emits a small SHP projection.
- [src/operations-profile.mjs](./src/operations-profile.mjs) validates declaration profiles for being/doing/working/governing, process/procedure/derivation/inquiry work types, operations-loop stage readings, process/procedure records, ledgers, budgets, cost, stationarity, and Laplacianization against [library/operations/specification.md](./library/operations/specification.md).
  It does not inspect live host processes, balance real ledgers, enforce resource consumption, compute Laplacians, or prove the operations derivation.
- [src/operations-records.mjs](./src/operations-records.mjs) validates finite operations-record bundles for process, procedure, work-event, budget, ledger-posting, cost-event, and operations-loop records against [library/operations/specification.md](./library/operations/specification.md).
  It does not inspect live host processes, enforce budgets, compute real ledger balances, or prove operating-layer settlement.
- [src/canonical-identity-profile.mjs](./src/canonical-identity-profile.mjs) validates declaration profiles for row IDs, RFC 8259/RFC 7493/RFC 8785 preconditions, RFC 8032 signature input, RFC 7464 stream item identity, and RFC 3339 timestamp policy against [CANONICAL-IDENTITY.md](./CANONICAL-IDENTITY.md).
  It does not implement a complete JCS canonicalizer, duplicate-detecting parser, timestamp parser, or cryptographic verifier.
- [src/trace-monoid-settlement-profile.mjs](./src/trace-monoid-settlement-profile.mjs) checks declaration-level trace monoid settlement profiles against [TRACE-MONOID-SETTLEMENT.md](./TRACE-MONOID-SETTLEMENT.md).
  It does not compute Foata normal forms, infer independence from raw rows, execute closure, or prove live swarm convergence.
- [src/predication-stage-profile.mjs](./src/predication-stage-profile.mjs) validates declaration profiles for the four predication-stage categories, finite-only FOUR placement, and prelocutionary boundary preservation.
- [src/prelocutionary-ingress-profile.mjs](./src/prelocutionary-ingress-profile.mjs) validates declaration profiles for token/claim/utterance ingress, articulating's aperiodic codomain, locutionary handler classes, and parse-before-illocution boundaries against [PRELOCUTIONARY-INGRESS.md](./PRELOCUTIONARY-INGRESS.md).
  It does not prove token-before-claim ordering, articulating category generation, or real handler correctness.
- [src/io-articulation-profile.mjs](./src/io-articulation-profile.mjs) validates declaration profiles for I/O as articulation, LLM/outside-system boundaries, unresolved or partial function handling, and standards binding after object-boundary derivation against [IO-ARTICULATION.md](./IO-ARTICULATION.md).
  It does not validate live LLM behavior, inspect HTTP traffic, verify signatures, or execute settlement.
- [src/proof-tree-irresolution-profile.mjs](./src/proof-tree-irresolution-profile.mjs) validates declaration profiles for SPOTCOMP as a proof tree that keeps unresolved or partial functions typed, replayable, and auditable against [PROOF-TREE-IRRESOLUTION.md](./PROOF-TREE-IRRESOLUTION.md).
  It does not prove the active tree, inspect live catalogs, compute closure, validate outside systems, verify signatures, or decide cohomology.
- [src/implementation-core-profile.mjs](./src/implementation-core-profile.mjs) validates declaration profiles for the consolidated implementation core against [library/implementation/specification.md](./library/implementation/specification.md): exact EAVT rows, JSONL item identity, canonical row IDs, append/G-Set merge, admission gates, TRC/TDP replay, PAM closure, SHP packet projection, wire/federation morphisms, modeled-player runtime, operations witnesses, minimum runtime components, and non-conformance boundaries.
  It does not implement canonical JSON, inspect live files, execute closure, verify signatures, or prove the open derivation obligations.
- [src/predication-fiber-profile.mjs](./src/predication-fiber-profile.mjs) validates declaration profiles for general predication fiber algebra, fibration, hyperdoctrine, FOUR specialization, and implementation boundary.
  It does not prove twist-product residuation, generator exhaustiveness, Beck-Chevalley, Frobenius, or comprehension.
- [src/predication-fiber-quantifier-profile.mjs](./src/predication-fiber-quantifier-profile.mjs) validates declaration profiles for reindexing `f*`, existential left adjoints, universal right adjoints, knowledge/truth order separation, and finite-probe boundaries against [PREDICATION-FIBER-QUANTIFIERS.md](./PREDICATION-FIBER-QUANTIFIERS.md).
  It does not prove the full hyperdoctrine, specialization quantifiers, Beck-Chevalley, Frobenius, comprehension, or arbitrary-`L` correctness.
- [src/closure-settling-profile.mjs](./src/closure-settling-profile.mjs) validates declaration profiles for closure 2-monad axioms, the closure-plus-increment settling endofunctor, closure-merge bridge, apex evidence, sigma/delta cycle, local-settling restriction, bounded-fuel partiality, and finite-only FOUR placement.
  It does not compute closure or prove the fixed-point theorem.
- [src/chl-language-profile.mjs](./src/chl-language-profile.mjs) validates declaration profiles for CHL language-cone structure, distinct column morphisms, scoped cross-tradition coincidence, path-theory/Yoneda obligations, and the pure-morphism/wrapper boundary.
  It does not prove the coincidence theorem or the path-theory cone-leg.
- [src/generator-variance-profile.mjs](./src/generator-variance-profile.mjs) validates declaration profiles for extension embeddings, restriction frontiers, coincidence scopes, required local examples, and implementation boundaries against [GENERATOR-VARIANCE.md](./GENERATOR-VARIANCE.md).
  It does not prove the embeddings, restriction functoriality, coincidence theorems, or EAVT audit vocabulary.
- [src/trace-axis-profile.mjs](./src/trace-axis-profile.mjs) validates declaration profiles for rich trace axes, exact EAVT event rows, causal/provenance support, trace-monoid independence, directed joins, and projection axis boundaries.
- [src/recognition-profile.mjs](./src/recognition-profile.mjs) validates declaration profiles for trace-axis recognition fiber, shape-recognition limits, local admission gates, swarm role recognition, and CGS admission boundaries against [RECOGNITION.md](./RECOGNITION.md).
  It does not prove recognition-cell settlement, governance modal restriction, CGS strategy laws, or the information-to-CGS functor.
- [src/positing-profile.mjs](./src/positing-profile.mjs) validates declaration profiles for categorical positing, naturality, speech-act factorization, EAVT event presentation, and downstream effect boundaries.
- [src/envelope.mjs](./src/envelope.mjs) signs and verifies Ed25519 federation envelopes over canonical JSON payloads.
- [src/swarm.mjs](./src/swarm.mjs) exercises a minimal signed-envelope ingestion loop.
- [src/federation-admission-profile.mjs](./src/federation-admission-profile.mjs) validates declaration profiles for receiver-side federation admission against [library/wire-federation/specification.md](./library/wire-federation/specification.md): representation receipt, canonical identity, signature verification, ordered local gates, regime binding, outcomes, audit/problem evidence, and non-conformance boundaries.
  It does not validate live HTTP, run TLS, implement a complete JSON parser, verify real signatures, or execute local settlement.
- [src/swarm-runtime-profile.mjs](./src/swarm-runtime-profile.mjs) validates declaration profiles for the swarm runtime loop against [library/swarm-runtime/specification.md](./library/swarm-runtime/specification.md): swarm object positions over `(O, V, r)`, federation admission gates, trace store state, player-local loops, modeled-player state, CGS/ludic handoff, packet/wire boundaries, operations/governance/cost, bigraded/aperiodic obligations, standards boundaries, and non-conformance cases.
  It does not validate a live swarm, compute closure, verify real signatures, execute CGS composition, or prove final SPOTCOMP conformance.
- [src/information-profile.mjs](./src/information-profile.mjs) checks declaration-level settling-to-information profiles against [SETTLING-INFORMATION.md](./SETTLING-INFORMATION.md).
  It does not prove the category of informational artifacts, closure-rule correctness, aboutness closure completeness, or SHP projection correctness.
- [src/information-computer-profile.mjs](./src/information-computer-profile.mjs) checks declaration-level information-to-computers profiles against [INFORMATION-COMPUTERS.md](./INFORMATION-COMPUTERS.md).
  It does not prove actual schema validation, append-only behavior, script determinism, canonicalization implementation correctness, or federation convergence.
- [src/posix-profile.mjs](./src/posix-profile.mjs) checks declaration-level computers-to-POSIX profiles against [COMPUTERS-POSIX.md](./COMPUTERS-POSIX.md).
  It does not inspect real filesystem state, enforce append flags, execute processes, validate byte encodings, or prove path hom-functor equality.
- [src/path-typing.mjs](./src/path-typing.mjs) checks declaration-level path-role manifests against the candidate [PATH-TYPING.md](./PATH-TYPING.md) surface.
  It does not inspect a full resource tree.
- [src/trc-layout.mjs](./src/trc-layout.mjs) checks declaration-level TRC layout profiles against [TRC-LAYOUT.md](./TRC-LAYOUT.md).
  It does not inspect real POSIX files, append-only behavior, ESM exports, or behavioral monotonicity.
- [src/regime-federation.mjs](./src/regime-federation.mjs) checks declaration-level regime/payload compatibility for [REGIME-FEDERATION.md](./REGIME-FEDERATION.md).
  It does not compute closure ordinals or cohomology.
- [src/cohomology-audit-profile.mjs](./src/cohomology-audit-profile.mjs) checks declaration-level bigraded cohomology audit profiles against [COHOMOLOGY-AUDIT.md](./COHOMOLOGY-AUDIT.md).
  It does not compute cohomology, prove vanishing, derive top-cell membership, or validate cached cohomology values.
- [src/agentic-profile.mjs](./src/agentic-profile.mjs) checks declaration-level agentic embedding profiles against [AGENTIC-EMBEDDING.md](./AGENTIC-EMBEDDING.md).
  It does not prove skill admissibility, governance algebra, recognition settlement, behavioral-space inclusion, or CGS strategy correctness.
- [src/player-character-profile.mjs](./src/player-character-profile.mjs) checks declaration-level player/character boundary profiles against [PLAYER-CHARACTER-BOUNDARY.md](./PLAYER-CHARACTER-BOUNDARY.md).
  It does not prove local-settling correctness, skill admissibility, modal governance, host installation correctness, CGS receptivity, or strategy composition.
- [src/governance-profile.mjs](./src/governance-profile.mjs) checks declaration-level governance profiles against [GOVERNANCE.md](./GOVERNANCE.md).
  It does not prove modal restriction, capability-fiber implication, non-amplification, or finite-settlement correctness.
- [src/cgs-profile.mjs](./src/cgs-profile.mjs) checks declaration-level CGS modeled-player profiles against [CGS-EMBEDDING.md](./CGS-EMBEDDING.md).
  It does not prove full CGS embedding, receptivity, innocence, strategy composition, or symmetry-groupoid laws.
- [src/cgs-strategy-laws-profile.mjs](./src/cgs-strategy-laws-profile.mjs) checks declaration-level CGS strategy-law profiles against [CGS-STRATEGY-LAWS.md](./CGS-STRATEGY-LAWS.md).
  It does not prove receptivity, interaction-and-hiding composition, symmetry quotient correctness, innocence, full abstraction, or final modeled-player embedding.
- [src/bigraded-diamond-swarm-profile.mjs](./src/bigraded-diamond-swarm-profile.mjs) checks declaration-level bigraded diamond swarm profiles against [BIGRADED-DIAMOND-SWARMS.md](./BIGRADED-DIAMOND-SWARMS.md).
  It does not prove the KZ diamond, compute common knowledge, compute cohomology, derive concrete aperiodic tilings, validate DRIP exchanges, or close the CGS embedding.
- [src/aperiodic-swarm-witness-profile.mjs](./src/aperiodic-swarm-witness-profile.mjs) checks declaration-level aperiodic swarm witness profiles against [APERIODIC-SWARM-WITNESS.md](./APERIODIC-SWARM-WITNESS.md).
  It does not compute cohomology, prove MLD-equivalence, build an Anderson-Putnam complex, decide weight-stability, or validate a live swarm.
- [src/moduli-descent-laplacian-profile.mjs](./src/moduli-descent-laplacian-profile.mjs) checks declaration-level moduli/descent/Laplacian profiles against [MODULI-DESCENT-LAPLACIAN.md](./MODULI-DESCENT-LAPLACIAN.md).
  It does not compute cohomology, prove descent, decide a rule-language fragment, construct a bitopological settling site, prove Verdier duality, or validate strong MLD for a live swarm.
- [src/regime-substitution-ladder-profile.mjs](./src/regime-substitution-ladder-profile.mjs) checks declaration-level regime substitution ladder profiles against [REGIME-SUBSTITUTION-LADDER.md](./REGIME-SUBSTITUTION-LADDER.md).
  It does not compute substitution cohomology, classify a live rule system, construct the meta-moduli stack, or prove a live swarm's strong MLD class.
- [src/realizability-deformation-profile.mjs](./src/realizability-deformation-profile.mjs) checks declaration-level realizability/deformation profiles against [REALIZABILITY-DEFORMATION.md](./REALIZABILITY-DEFORMATION.md).
  It does not compute cohomology, decide realizability, calculate Ext groups, derive a live tangent space, or prove CHL stabilization for a live swarm.
- [src/void-relationlessness-profile.mjs](./src/void-relationlessness-profile.mjs) checks declaration-level void relationlessness profiles against [VOID-RELATIONLESSNESS-STAGES.md](./VOID-RELATIONLESSNESS-STAGES.md).
  It does not compute void filtrations, cohomology, rank stability, or live relationless frontiers.
- [src/drip-uas-profile.mjs](./src/drip-uas-profile.mjs) checks declaration-level DRIP/UAS binding profiles against [DRIP-UAS-BINDING.md](./DRIP-UAS-BINDING.md).
  It does not validate live RID broadcasts, query DNS, verify DET cryptographic material, implement ASTM or civil-aviation rules, or prove modeled-player swarm conformance.
- [src/information-game-profile.mjs](./src/information-game-profile.mjs) checks declaration-level information-to-games profiles against [INFORMATION-GAMES.md](./INFORMATION-GAMES.md).
  It does not prove the information-to-CGS functor, event-structure completeness, strategy receptivity, innocence, interaction-and-hiding composition, or symmetry-groupoid laws.
- [src/wire-profile.mjs](./src/wire-profile.mjs) checks declaration-level wire profiles against [WIRE-PROFILES.md](./WIRE-PROFILES.md).
  It does not register media types, validate live HTTP exchanges, run TLS, or prove cryptographic implementation correctness.
- [src/shp-profile.mjs](./src/shp-profile.mjs) checks declaration-level SHP profiles against [SHP.md](./SHP.md).
  It does not prove the SHP object derivation, full RFC 7992 conformance, HTML parser correctness, or projection-morphism placement.

The useful evidence supplied by this code is limited to local checks of candidate laws such as append monotonicity, merge idempotence, and signature-before-merge.
Production implementations should use a tested RFC 8785 implementation.
The probe rejects unsupported JavaScript values but does not replace a full JSON parser with duplicate-key detection.
