# Gaps And Proof Obligations

This file is intentionally normative-adjacent: implementations can satisfy local probe requirements while these items remain open, but they MUST NOT claim final SPOTCOMP conformance while the relevant gaps are open.

## 0. Sub-Specification Family

The workspace still needs the actual specification family split out under `library/`.

Needed:

- complete PAM specification after the current skeleton;
- TRC/TDP specification for typed resources, closure-rule programs, dual filing, catalog replay, and execution to fixed point;
- SHP specification aligned with current packet terminology;
- wire/federation specification separated from MAS legacy vocabulary;
- complete modeled-player and CGS specifications after the current skeletons, including exact handoff objects;
- complete swarm-runtime specification after the current skeleton, including live admission, observation, replay, strategy, and audit profiles;
- conformance ownership matrix for every requirement.

Current candidate surface: [library/pam/specification.md](./library/pam/specification.md), [library/trc-tdp/specification.md](./library/trc-tdp/specification.md), [library/operations/specification.md](./library/operations/specification.md), [library/cgs/specification.md](./library/cgs/specification.md), [library/modeled-player/specification.md](./library/modeled-player/specification.md), [library/implementation/specification.md](./library/implementation/specification.md), [NORMATIVE-FUNCTIONS.md](./NORMATIVE-FUNCTIONS.md), [FUNCTION-LAWS.md](./FUNCTION-LAWS.md), [OPERATIONAL-MATH-FUNCTIONS.md](./OPERATIONAL-MATH-FUNCTIONS.md), [TRACE-PACKET-TRANSPORT.md](./TRACE-PACKET-TRANSPORT.md), [library/swarm-runtime/specification.md](./library/swarm-runtime/specification.md), [library/shp/specification.md](./library/shp/specification.md), [library/wire-federation/specification.md](./library/wire-federation/specification.md), and [library/learning/specification.md](./library/learning/specification.md).
PAM is established as Predicate Algebra Modeling; TRC/TDP is established as the same on-disk Typed Resource Catalog / Theory Derivation Program object; CGS, modeled-player, implementation-core, trace/packet/transport, swarm-runtime, SHP, wire/federation, and learning now have owning skeletons.
The basic function surface now names parse, identify, append, dual-file, merge, replay, posit, close, settle, project, read, transport, and admit as TRC/TDP operations over JSONL EAVT SPOTs, the subject-predicate-object cell traces, while the operational function surface specifies articulation/reification, fiber operations, reindexing adjoints, positing, closure, recognition/admission, modeled-player stepping, learning, and operational cost/budget/ledger functions.
These skeletons do not yet provide full schemas, examples, checker code, executable mathematical algorithms, or proofs for the whole sub-specification family.

## 0a. Operations Specification

The workspace now has an operations skeleton, but not a complete operating standard.

Needed:

- schemas for process, procedure, work event, budget, posting, and operations-loop records;
- proof that being/doing/working/governing are the right operational refinements of the Hoare strata;
- proof or refinement of process/procedure/derivation/inquiry as work types;
- ledger projection theorem from witnesses to balanced postings;
- budget exhaustion theorem as governed transition;
- Lawvere-quantale cost profile for SPOTCOMP settlement;
- stationarity and Laplacianization handoff into moduli/descent/Laplacian resources.

Current candidate surface: [library/operations/specification.md](./library/operations/specification.md), [schema/operations-profile.schema.json](./schema/operations-profile.schema.json), [src/operations-profile.mjs](./src/operations-profile.mjs), [schema/operations-records.schema.json](./schema/operations-records.schema.json), and [src/operations-records.mjs](./src/operations-records.mjs).
The profile checker validates declaration shape and the records checker validates finite operations-record bundles for process, procedure, work event, budget, ledger posting, cost event, and operations-loop references.
They do not inspect live processes, prove ledger balancing, enforce resource consumption, compute Laplacians, or prove the operations theory.

## 1. Full CGS Embedding

The local notes identify concurrent games with symmetry as the theory-of-computing layer.
This profile uses that reading for modeled players, but does not prove the full embedding of SPOTCOMP traces, settlements, and federation into CGS.

Needed:

- event-structure definition for EAVT append, observe, settle, and federate events;
- polarity assignment;
- conflict relation;
- symmetry groupoid;
- strategy equivalence notion;
- proof that trace merge respects the symmetry quotient.

Current candidate surface: [library/cgs/specification.md](./library/cgs/specification.md), [CGS-EMBEDDING.md](./CGS-EMBEDDING.md), [INFORMATION-GAMES.md](./INFORMATION-GAMES.md), [src/cgs-profile.mjs](./src/cgs-profile.mjs), and [src/information-game-profile.mjs](./src/information-game-profile.mjs) define declaration checks for events, causality, minimal conflicts, polarity, symmetry-class references, strategy bounds, receiver-relative information, observation maps, and arena observation bindings.
They do not close this gap.

Current strategy-law surface: [library/cgs/specification.md](./library/cgs/specification.md), [CGS-STRATEGY-LAWS.md](./CGS-STRATEGY-LAWS.md), and [src/cgs-strategy-laws-profile.mjs](./src/cgs-strategy-laws-profile.mjs) check declarations for CGS morphism arena shape, receptivity, symmetry quotienting, interaction-and-hiding composition, and sequential/innocent restrictions.
They do not prove these laws or the trace-merge symmetry quotient.

Current player/character boundary surface: [library/modeled-player/specification.md](./library/modeled-player/specification.md), [PLAYER-CHARACTER-BOUNDARY.md](./PLAYER-CHARACTER-BOUNDARY.md), and [src/player-character-profile.mjs](./src/player-character-profile.mjs) check that external players, modeled players, characters, personas, roles, skills, method/tool surfaces, and CGS strategies remain distinct before a swarm record is treated as modeled-player evidence.
They do not prove local-settling correctness, skill admissibility, modal governance, host installation correctness, CGS receptivity, or strategy composition.

Current swarm-runtime surface: [library/swarm-runtime/specification.md](./library/swarm-runtime/specification.md), [SWARM-FUNCTIONS.md](./SWARM-FUNCTIONS.md), and [src/swarm-runtime-profile.mjs](./src/swarm-runtime-profile.mjs) state the implementable swarm loop as both runtime surfaces and compositions of the basic TRC/TDP functions.
They do not validate a live swarm or close the CGS, bigraded, aperiodic, or modeled-player proof gaps.

## 2. Categorical Machinery Checkers

[CATEGORICAL-MACHINERY.md](./CATEGORICAL-MACHINERY.md) identifies source-backed invariants that are not yet executable conformance checks.

Needed:

- trace-axis declaration and preservation checks;
- positing-naturality checks across reindexing and projection;
- closure-2-monad/least-fixed-point evidence;
- regime/cohomology audit hooks;
- local-settling-to-modeled-player checker.
- CGS receptivity, strategy composition, and symmetry-groupoid checks.
- information-to-game functor checks for observation restrictions and event-structure generation.

Current trace-axis candidate surface: [TRACE-AXES.md](./TRACE-AXES.md) and [src/trace-axis-profile.mjs](./src/trace-axis-profile.mjs) check declarations for the six rich trace axes, exact EAVT event rows, causal/provenance accumulativity, trace-monoid independence, directed event-union joins, and projection preservation/forgetting.
They do not derive trace from positing, prove projection naturality, or prove the trace-monoid-to-settlement functor.

Current recognition candidate surface: [RECOGNITION.md](./RECOGNITION.md) and [src/recognition-profile.mjs](./src/recognition-profile.mjs) check declarations for recognition as trace axis, shape-recognition limits, receiver-relative admission, swarm role recognition, and CGS admission gates.
They do not prove recognition-cell settlement or derive the rejected-admission conflict/cohomology mapping.

Current canonical-identity candidate surface: [CANONICAL-IDENTITY.md](./CANONICAL-IDENTITY.md) and [src/canonical-identity-profile.mjs](./src/canonical-identity-profile.mjs) check declarations for JCS row IDs, duplicate-name rejection, signature bytes, JSON text sequence item identity, and timestamp policy.
They do not implement a full RFC 8785 canonicalizer, duplicate-detecting parser, or timestamp parser.

Current positing-boundary candidate surface: [POSITING.md](./POSITING.md) and [src/positing-profile.mjs](./src/positing-profile.mjs) check declarations for Scott-continuous least-extension positing, naturality generator actions, datum preservation, locution/illocution/perlocution separation, exact EAVT event presentation, and downstream records/logs/closure.
They do not prove naturality, derive the general `L` datum schema, or formalize batch projection naturality.

Current predication-stage candidate surface: [PREDICATION-STAGES.md](./PREDICATION-STAGES.md) and [src/predication-stage-profile.mjs](./src/predication-stage-profile.mjs) check declarations for articulating as aperiodic predication category, predicating as transfinite predication category, positing as Scott-continuous predication category, and settling as finite predication category.
They do not prove the functors between those stage categories.

Current prelocutionary ingress candidate surface: [PRELOCUTIONARY-INGRESS.md](./PRELOCUTIONARY-INGRESS.md) and [src/prelocutionary-ingress-profile.mjs](./src/prelocutionary-ingress-profile.mjs) check declarations for token/claim/utterance grounding, articulating ingress, locutionary handler classes, and parse-before-illocution boundaries.
They do not prove token-before-claim ordering, articulating category generation, or real handler correctness.

Current I/O articulation candidate surface: [IO-ARTICULATION.md](./IO-ARTICULATION.md) and [src/io-articulation-profile.mjs](./src/io-articulation-profile.mjs) check declarations for external I/O, LLM prompts/completions, hidden context, tool calls, unresolved inputs, and standards bindings as articulation-boundary material.
They do not validate live outside systems, prove articulating category generation, verify signatures, or execute settlement.

Current proof-tree irresolution candidate surface: [PROOF-TREE-IRRESOLUTION.md](./PROOF-TREE-IRRESOLUTION.md) and [src/proof-tree-irresolution-profile.mjs](./src/proof-tree-irresolution-profile.mjs) check declarations for recursion grounding, stage preservation, partial-map/default discipline, fixed-point versus prefix outcomes, TRC/TDP replay, outside-system limits, and standards placement.
They do not prove the active tree, compute closure, inspect live catalogs, validate outside systems, verify signatures, or decide cohomology.

Current closure/settling apex candidate surface: [CLOSURE-SETTLING.md](./CLOSURE-SETTLING.md) and [src/closure-settling-profile.mjs](./src/closure-settling-profile.mjs) check declarations for closure 2-monad axioms, settling endofunctor formula, closure-merge commutation, Knaster-Tarski apex evidence, sigma/delta pass roles, local settling as bounded restriction, bounded-fuel partiality, and finite-only FOUR placement.
They do not compute closure, prove the fixed-point theorem, lift closure-merge commutation to the full 2-categorical setting, or decide closure ordinals.

Current CHL language-cone candidate surface: [CHL-LANGUAGE-CONES.md](./CHL-LANGUAGE-CONES.md) and [src/chl-language-profile.mjs](./src/chl-language-profile.mjs) check declarations for CHL language apex, required cone legs, distinct morphism positions, scoped cross-tradition coincidence, path-theory/Yoneda obligations, and the pure-morphism/wrapper boundary.
They do not prove the cross-tradition coincidence theorem, derive the full path-theory cone-leg, or prove Yoneda.

Current predication-fiber candidate surface: [PREDICATION-FIBER-ALGEBRA.md](./PREDICATION-FIBER-ALGEBRA.md), [PREDICATION-FIBER-QUANTIFIERS.md](./PREDICATION-FIBER-QUANTIFIERS.md), [src/predication-fiber-profile.mjs](./src/predication-fiber-profile.mjs), and [src/predication-fiber-quantifier-profile.mjs](./src/predication-fiber-quantifier-profile.mjs) check declarations for `A_p = (L x L)^(E x E)`, pointwise bilattice/residuated operations, fibration A1-A3, hyperdoctrine B1-B4, reindexing `f*`, existential/universal adjoints over knowledge and truth orders, FOUR as boolean specialization, and implementation rules that keep non-FOUR fibers legal.
They do not prove twist-product residuation, predicate-generator exhaustiveness, Beck-Chevalley, Frobenius, comprehension, specialization quantifier adjoints, or the full arbitrary-`L` theorem.

Current generator-variance candidate surface: [GENERATOR-VARIANCE.md](./GENERATOR-VARIANCE.md) and [src/generator-variance-profile.mjs](./src/generator-variance-profile.mjs) check declarations for extension embeddings, restriction frontiers, scoped coincidence, required local examples, and implementation boundaries that reject unknown variance as strong evidence.
They do not prove embeddings, restriction functoriality, or coincidence theorems.

Current realizability/deformation candidate surface: [REALIZABILITY-DEFORMATION.md](./REALIZABILITY-DEFORMATION.md) and [src/realizability-deformation-profile.mjs](./src/realizability-deformation-profile.mjs) check declarations for the meta-realizability map, increment-sequence fibers, realizability axes, predicate-naturality coupling, deformation tangent data, and CHL-stabilization scope.
They do not compute cohomology, decide realizability, calculate Ext groups, derive a live tangent space, or prove CHL stabilization for a live swarm.

## 3. Trace Monoid To Settlement Lattice

The active tree marks this as open: independent positing steps form a trace monoid, but the functor from abstract history systems to valuation lattices is not fully derived.

This profile requires operational commutation and CRDT merge only.

Current trace-monoid candidate surface: [TRACE-AXES.md](./TRACE-AXES.md) records the independence relation and checks that declared independent steps are irreflexive and causally unordered.
It does not derive the valuation-lattice functor.

Current history-action candidate surface: [TRACE-MONOID-SETTLEMENT.md](./TRACE-MONOID-SETTLEMENT.md) and [src/trace-monoid-settlement-profile.mjs](./src/trace-monoid-settlement-profile.mjs) require declarations for trace-monoid construction, independence evidence, valuation action, Foata/prefix summaries, CRDT convergence scope, and order/federation boundaries.
They do not compute normal forms, infer independence, or execute closure.

## 4. Regime-Aware Federation

[REGIME-FEDERATION.md](./REGIME-FEDERATION.md) defines candidate declaration and compatibility rules, but it does not compute closure ordinals, trajectory equivalence, or cohomology.

Needed:

- closure-ordinal checker for declared rule systems;
- trajectory-prefix format with ordinal/stage typing;
- cohomology audit checker for `H1_t`, `H1_top`, and optional K4 sectors;
- envelope binding so federation payloads carry regime profiles by signature;
- downgrade behavior tests for receivers that cannot verify a claimed regime.

Current cohomology-audit candidate surface: [COHOMOLOGY-AUDIT.md](./COHOMOLOGY-AUDIT.md) and [src/cohomology-audit-profile.mjs](./src/cohomology-audit-profile.mjs) check declarations for designation grades, cohomological degree slots, `H1_t`, `H1_top`, inconsistency-sheaf records, optional FOUR/K4 projections, and downgrade policy.
They do not compute cohomology, prove vanishing, or decide top-cell membership from raw traces.

## 5. Extension/Restriction Path Derivation

The category/generator/codomain discipline now has a candidate checker surface in [PATH-TYPING.md](./PATH-TYPING.md), but a complete checker is not yet implemented or proved.

Needed:

- path grammar for category roots, generators, and codomains;
- local proof objects showing whether each generator extends or restricts;
- validation that a finite projection artifact is downstream of its source trace.
- real catalog inspection for schema/log/script co-location, import aliases, and dual filing.

Current generator-variance surface: [GENERATOR-VARIANCE.md](./GENERATOR-VARIANCE.md) turns the second item into checkable declaration obligations, but the local proof objects and full catalog audit remain open.

## 6. Information Chunk

The user identified a large underived chunk between settling and computers: "information".
This profile names it but does not derive it.

Needed:

- information as a category downstream of settlement;
- document as an information-level object, not a SPOTCOMP packet format;
- SHP as the semantic hypertext projection object;
- proof that SHP projection is a finite settled projection of the relevant trace frontier.

See [CHUNK-MAP.md](./CHUNK-MAP.md) for the broader chunk chain.

Current candidate surface: [SETTLING-INFORMATION.md](./SETTLING-INFORMATION.md) and [src/information-profile.mjs](./src/information-profile.mjs) check declarations for discourse scopes, informational artifacts, uncertainty reduction, aboutness participation, document provenance, aboutness closure links, and SHP projection bindings.
They do not prove the category of informational artifacts, closure-rule correctness, aboutness closure completeness, or SHP projection correctness.

Current SHP candidate surface: [SHP.md](./SHP.md) and [src/shp-profile.mjs](./src/shp-profile.mjs) check declarations for SHP packet objects, projection/markup directions, class-as-morphism identity, `data-*` carrier attributes, RFC 7992 inhabitant constraints, and packet safety.
They do not prove the SHP object derivation, full byte-level HTML validation, or projection-morphism placement.

## 7. Computers, POSIX, Agents, And Games

The chunk chain beyond information is not fully derived.

Needed:

- information-to-computer derivation for schema/log/script and EAVT carrier shape;
- computer-to-POSIX derivation for process, file, path, append, stdio, signal, and exit-status assumptions;
- POSIX-to-SPOTCOMP derivation for the path-theory column and TRC conformance;
- computer-to-agent derivation for tool use, planning, persistent state, governance, skills, and traces;
- information-to-game derivation for observations, event structures, strategies, and symmetry.

Current POSIX-to-SPOTCOMP candidate surface: [TRC-LAYOUT.md](./TRC-LAYOUT.md) and [src/trc-layout.mjs](./src/trc-layout.mjs) check declarations for co-location, imports, dual filing, and non-authoritative value indexes.
They do not close the POSIX or path-hom-functor obligations.

Current information-to-computers candidate surface: [INFORMATION-COMPUTERS.md](./INFORMATION-COMPUTERS.md) and [src/information-computer-profile.mjs](./src/information-computer-profile.mjs) check declarations for schema/log/script witnesses, exact EAVT carriers, canonical identity, append-only logs, G-Set merge, and non-authoritative value indexes.
They do not prove actual schema validation, append-only behavior, script determinism, canonicalization correctness, or federation convergence.

Current computers-to-POSIX candidate surface: [COMPUTERS-POSIX.md](./COMPUTERS-POSIX.md) and [src/posix-profile.mjs](./src/posix-profile.mjs) check declarations for catalog root, path category, regular files, UTF-8 resources, LF-delimited logs, append behavior, process supervision, stdio, signals, exit status, module loading, and failure surfacing.
They do not inspect real filesystem state, enforce append flags, execute processes, validate byte encodings, or prove path hom-functor equality.

Current computers-to-agents candidate surface: [AGENTIC-EMBEDDING.md](./AGENTIC-EMBEDDING.md) and [src/agentic-profile.mjs](./src/agentic-profile.mjs) check declarations for characters, skills, player bindings, and swarm recognition.
They do not close governance, recognition, skill admissibility, or behavioral-space proof obligations.

Current recognition candidate surface: [RECOGNITION.md](./RECOGNITION.md) and [src/recognition-profile.mjs](./src/recognition-profile.mjs) checks the admission boundary shared by trace rows, federated deliveries, modeled-player moves, and swarm roles.
It does not prove recognition settlement.

Current information-to-games candidate surface: [INFORMATION-GAMES.md](./INFORMATION-GAMES.md) and [src/information-game-profile.mjs](./src/information-game-profile.mjs) check declarations for informational objects, observation maps, arena observation bindings, local strategy bindings, and federation composition.
They do not prove the information-to-CGS functor, event-structure completeness, conflict inheritance, receptivity, innocence, or symmetry-groupoid laws.

Current CGS strategy-law candidate surface: [CGS-STRATEGY-LAWS.md](./CGS-STRATEGY-LAWS.md) and [src/cgs-strategy-laws-profile.mjs](./src/cgs-strategy-laws-profile.mjs) isolate the morphism-level strategy obligations that this branch must eventually prove.

Current void-relationlessness candidate surface: [VOID-RELATIONLESSNESS-STAGES.md](./VOID-RELATIONLESSNESS-STAGES.md) and [src/void-relationlessness-profile.mjs](./src/void-relationlessness-profile.mjs) translate old void-cone/failure-geometry material into the four stage categories.
They do not compute live void filtrations, apex pairings, permanent relationless frontiers, or weighted rank stability.

## 8. Bigraded Diamond Swarm Mathematics

The modeled-player layer now has an additional blocker from the lab predication-categories material.

Needed:

- proof-backed KZ-diamond strict commutation on the common settling 2-category;
- preservation of truth-axis and knowledge-axis common-knowledge fixed points;
- bigraded cohomology audit preservation for `H1_t` and `H1_top`;
- multi-observer-system functor from modeled players into local settlings;
- aperiodic tiling witness format for non-periodic swarm claims;
- standards boundary showing UAS Remote ID/DRIP conformance independently of tiling.

Current candidate surface: [BIGRADED-DIAMOND-SWARMS.md](./BIGRADED-DIAMOND-SWARMS.md) and [src/bigraded-diamond-swarm-profile.mjs](./src/bigraded-diamond-swarm-profile.mjs).
They block strong swarm conformance when bigrading or tiling evidence is unknown.

Current aperiodic-witness surface: [APERIODIC-SWARM-WITNESS.md](./APERIODIC-SWARM-WITNESS.md) and [src/aperiodic-swarm-witness-profile.mjs](./src/aperiodic-swarm-witness-profile.mjs) refine the tiling evidence into substitution, direct-limit, MLD, classifying-invariant, bilattice-alignment, and weighted-stability declarations.
They do not compute the invariants.

## 9. Canonical Media Types

JSONL is on-disk only.
The exact media type registration strategy for SPOTCOMP traces and envelopes is open.

Candidates:

- `application/json-seq` for RFC 7464 streaming;
- `application/spotcomp+json` for signed envelopes;
- `application/eavt+jsonl` only as an unregistered local file convention.

Current candidate surface: [WIRE-PROFILES.md](./WIRE-PROFILES.md) treats existing registered types as usable now and SPOTCOMP-specific `+json` names as unregistered candidates requiring a media-type registration obligation.
The receiver-side admission surface [src/federation-admission-profile.mjs](./src/federation-admission-profile.mjs) checks declaration bundles for representation receipt, canonical identity, signature verification, ordered local admission gates, regime binding, outcome/audit behavior, and HTTP problem details.
It does not validate live HTTP, run TLS, perform complete canonicalization, verify real signatures, or execute local settlement.

Current canonical identity surface: [CANONICAL-IDENTITY.md](./CANONICAL-IDENTITY.md) records that JSON text sequences have item-level identity only for signatures unless a manifest is signed.

## 10. Governance Semantics

Modeled players carry governance regimes and capability bounds, but this profile does not yet specify a full normative governance algebra.

Needed:

- authorization rows;
- capability delegation;
- revocation without destructive trace edits;
- finite governance settlement projection.

Current candidate surface: [GOVERNANCE.md](./GOVERNANCE.md) and [src/governance-profile.mjs](./src/governance-profile.mjs) check declarations for one modal restriction evaluator, the six authorization surfaces, exact EAVT authorization rows, non-amplifying delegation, revocation-as-new-row, side-effect gates, action bounds, and finite settlement projections.
They do not prove the modal restriction theorem, capability-fiber implication, cache coherence, governance vote validity, or settlement correctness.

## 11. Continuous Learning

SPOTCOMP now has a declaration surface for continuous learning, but not a full learning theory.

Needed:

- proof that the answering/referencing loop is Scott-continuous under the relevant closure operator;
- fixed-point theorem for skill improvement as closure over skill specifications;
- conformance theorem separating teaching, installation, memory retrieval, and durable learned-state evidence;
- closure-equivalence criterion for smooth rule learning versus transition;
- ludic/CGS theorem identifying when a learning step is a game move;
- operating-system contract for durable learning resources without collapsing modeled-player learning into host storage behavior.

Current candidate surface: [CONTINUOUS-LEARNING.md](./CONTINUOUS-LEARNING.md) and [src/continuous-learning-profile.mjs](./src/continuous-learning-profile.mjs) check declarations for answering/referencing, teaching, skill closure, memory fragments, rule learning, ludic/CGS boundaries, and implementation downgrades.
They do not prove learning quality, fixed points, closure equivalence, or live strategy preservation.
