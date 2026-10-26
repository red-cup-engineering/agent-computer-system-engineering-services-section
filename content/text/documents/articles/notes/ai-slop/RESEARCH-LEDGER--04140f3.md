# Research Ledger

Status: working ledger.
This file records repo-backed invariants that constrain SPOTCOMP.
It is not a final proof.

## 0. PAM Is Predicate Algebra Modeling

Source:

- `development/experimental/spotcomp/library/pam/specification.md`;
- `development/experimental/emsenn/active/hacking/spotcomp/HANDROLLED-SPOTCOMP-SPEC.html`;
- `lab/archive/research/operations/engineering/research/archive/esm-predication/README.md`;
- `lab/archive/research/operations/engineering/research/archive/esm-predication/docs/architecture/layering.md`;
- `lab/archive/research/operations/engineering/research/archive/esm-predication/docs/architecture/principles.md`.

Invariant:

PAM means Predicate Algebra Modeling.
It is the SPOTCOMP CPU/instruction-set view: reified SPO messages enter a model, declared morphisms dispatch across predicate fibers, settlement runs to a fixed point or declared partial boundary, and the returned answer is a witness configuration.

Implementation consequence:

The SPOTCOMP workspace needs a sub-specification family, not only broad declaration surfaces.
PAM now has an initial normative skeleton at [library/pam/specification.md](./library/pam/specification.md).
The skeleton also corrects the old finite runtime reading: FOUR is one finite PAM profile, not the universal value substrate.

## 0a. Operations Are Substrate Content

Source:

- `development/experimental/spotcomp/library/operations/specification.md`;
- `development/experimental/emsenn/active/hacking/spotcomp/HANDROLLED-SPOTCOMP-SPEC.html`;
- `lab/archive/relating-repo/relating-repo/operations/engineering/triage/operations/command/commands/rsc-quiescent/triage/work-orchestration/texts/goals/operations-loop.md`;
- `lab/archive/relating-repo/relating-repo/operations/engineering/triage/operations/command/commands/rsc-quiescent/triage/accounting/texts/chart-of-accounts.md`;
- `lab/archive/relating-repo/relating-repo/library/theories/engineering/theories/tech/theories/computing/theories/predicated-computing/concepts/cost-discipline.md`;
- `lab/archive/relating-repo/relating-repo/library/theories/engineering/theories/tech/theories/computing/theories/predicated-computing/theorems/cost-composition-via-lawvere-quantale.md`;
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/lawvere-laplacian-grothendieck-sites.md`.

Invariant:

The operating layer is not an external work manager.
Learning/doing/teaching are the Hoare/sigma-delta strata.
Doing refines into governing, planning, and working.
Planning/dispatch/execution/tracking/review/feedback is an operations loop over fixed fibers, history extension, global sections, and nucleus update.
Ledgers, budgets, and costs are substrate content with witness projections and Lawvere-quantale composition.

Implementation consequence:

The first operations skeleton is [library/operations/specification.md](./library/operations/specification.md).
The current declaration probe is [src/operations-profile.mjs](./src/operations-profile.mjs).
Implementation probes must not treat host processes, scripts, budgets, or ledgers as side state.
They need typed records and witness-preserving handoffs into settlement and Laplacian/stationarity machinery.

## 0b. I/O Enters As Articulation

Source:

- `development/experimental/spotcomp/IO-ARTICULATION.md`;
- `development/experimental/spotcomp/PRELOCUTIONARY-INGRESS.md`;
- `development/active/library/token/docs/dev/journal/2026-05-25.md`;
- `development/active/library/claim/docs/dev/journal/2026-05-25.md`;
- `development/active/library/utterance/docs/dev/journal/2026-05-25.md`;
- `development/active/articulating/articulating.schema.json`;
- `development/active/docs/dev/journal/2026-05-27.md`;
- `development/active/docs/dev/journal/2026-05-28.md`.

Invariant:

External I/O is not automatically SPOTCOMP evidence.
It is presentation material that must enter through token, claim, utterance, and articulating before predicating, positing, settling, or standards-bound wire behavior can make claims about it.
LLM prompts, completions, hidden context, and tool calls are outside-system presentations unless typed admission and modeled-player evidence say otherwise.

Implementation consequence:

[IO-ARTICULATION.md](./IO-ARTICULATION.md) and [src/io-articulation-profile.mjs](./src/io-articulation-profile.mjs) now record the declaration boundary.
Implementations must not treat parsers, API calls, model outputs, host exceptions, or silent defaults as proof-engine behavior.
Unresolved or partial functions remain typed proof-tree content, trajectory prefixes, or explicit downgrades.

## 0c. Irresolution Is Proof-Tree Content

Source:

- `development/experimental/spotcomp/PROOF-TREE-IRRESOLUTION.md`;
- `development/experimental/spotcomp/CLOSURE-SETTLING.md`;
- `development/experimental/spotcomp/library/trc-tdp/specification.md`;
- `development/active/docs/dev/journal/2026-05-27.md`;
- `development/active/docs/dev/journal/2026-05-28.md`;
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/library/predication-fibration/hacking/gauge-twisted-reindexing/docs/dev/journal/2026-05-24.md`.

Invariant:

SPOTCOMP does not treat an unresolved input, partial map, obstruction, timeout, unverifiable claim, or unsupported regime as a host-language accident.
Those states are proof-tree content: typed prefixes, bottom/default extensions, obstruction witnesses, cohomology audits, contradiction, abstention, or downgrade.
Final settlement requires fixed-point evidence.

Implementation consequence:

[PROOF-TREE-IRRESOLUTION.md](./PROOF-TREE-IRRESOLUTION.md) and [src/proof-tree-irresolution-profile.mjs](./src/proof-tree-irresolution-profile.mjs) now record the declaration boundary.
Implementations must not collapse partiality into exceptions, unchecked nulls, endpoint snapshots, parser success, or model output.
TRC/TDP replay is the mechanism that keeps unresolved cases typed and auditable.

## 1. EAVT Trace Substrate

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/trace-monoid/trace-monoid.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/trace-monoid/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/library/cell-record/library/cell-trace/cell-trace.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/library/predication-cell-trace/predication-cell-trace.md`

Invariant:

EAVT JSONL is the trace presentation.
The relevant algebraic object is a trace of positings, with independent positings commuting as a trace monoid.
The old habit of reading EAVT as an encoding of a distinguished FOUR value is not stable under the repo's trace/cell-trace material.
FOUR appears as a boolean-specialized fiber algebra, not as the substrate.

Implementation consequence:

SPOTCOMP federation must exchange trace rows or trajectory records.
Endpoint snapshots are admissible only when the regime discipline proves they preserve the relevant closure/cohomology invariants.

## 2. Fiber Algebra Generalizes FOUR

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration/library/predication-fiber-algebra/predication-fiber-algebra.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration/library/predication-fiber-algebra/docs/dev/journal/2026-05-24.md`

Invariant:

For a predicate `p`, the fiber is `A_p = (L x L)^(E x E)`, a pointwise twist product over an entity-pair index.
Boolean `L` yields the four Belnap corners; general `L` yields quantale, fuzzy, and continuous fibers.
The value stratum is therefore bilattice-residuated and fibered, not globally FOUR-shaped.

Implementation consequence:

Schemas must allow values whose settlement fiber is declared by the active predicate/fiber context.
A conformance checker may validate a FOUR projection, but it must not require every trace value to be a FOUR element.

## 3. Articulating To Settling Direction

Source:

- `development/docs/dev/journal/2026-05-27.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/positing/docs/dev/journal/2026-05-26.md`
- `development/emsenn/active/hacking/spotcomp/HANDROLLED-SPOTCOMP-SPEC.html`

Invariant:

The direction is `articulating -> predicating -> positing -> settling`, and the regime direction is aperiodic/transfinite toward finite settlement projections.
Finite settlement cannot be an upstream ontology for trace formation.

Implementation consequence:

`src/` may test finite laws, but final SPOTCOMP conformance must derive finite artifacts from traces, not traces from the artifact format or implementation convenience.

## 4. Initial Objects, Generators, And Path Derivation

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/initial-algebra-tower/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/path-category/path-category.schema.json`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/library/initial-object/initial-object.md`

Invariant:

Repository placement is proof-tree placement.
A `library/$thing/` root is an initial object for the category being generated; `$thing/$morphism/` is a generator; `$thing/library/$object/` is a codomain object.
POSIX path identity participates in this proof tree through the path category, whose root is initial.

Implementation consequence:

SPOTCOMP tooling needs a path-typing checker before it can claim normative resource layout conformance.
Object-oriented inheritance readings are malformed for this substrate.

## 5. Extension And Restriction Are Load-Bearing

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-cell/slicing-to-predication-cell-trace/slicing-to-predication-cell-trace.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/docs/dev/journal/2026-05-27.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/concepts/closure-kind.md`

Invariant:

Extension adds admissible structure or product positions.
Restriction selects a fiber, subcategory, frontier, or certified view.
The operation kind is not a naming convention; it determines the shape of the codomain and the proof obligations for that path.

Implementation consequence:

Every managed generator needs an extension/restriction declaration with evidence.
Unknown generator variance must block strong conformance.

## 6. CHL Apex Recursion And Initial Algebra Towers

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/hacking/library/chl-apex-recursion/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/hacking/library/chl-apex-recursion/hacking/library/apex/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/hacking/library/chl-apex-recursion/hacking/library/chl-stratum/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/hacking/library/chl-apex-recursion/hacking/library/lambek-lemma/docs/dev/journal/2026-05-26.md`

Invariant:

Each CHL stratum is organized as an apex produced by a closure operator's least fixed point and as an initial algebra of the relevant endofunctor.
Lambek's lemma supplies the fixed-point/initial-algebra isomorphism.
Language columns and morphism positions remain distinct unless a coincidence theorem proves a specialization.

Implementation consequence:

The spec must not collapse predicating, positing, settling, proof, term-instantiation, and existential push-forward into one morphism.
It must state the coincidence conditions separately.

## 7. Regime Discipline

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-settling-category/library/predication-settling/hacking/library/four-regime-dichotomy/docs/dev/journal/2026-05-24.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/code/structures/regime-record.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/code/structures/event-log.md`

Invariant:

The four regimes are closure-ordinal regimes: strict, Scott-continuous, transfinite-bounded, and aperiodic.
Strict and Scott-continuous regimes have trivial first cohomology for the settling-associated sheaf.
Transfinite-bounded and aperiodic regimes can have non-trivial first cohomology, so endpoint-state exchange can lose invariants; trajectory exchange is required.

Implementation consequence:

SPOTCOMP swarm federation must declare a regime record.
A receiver must reject or downgrade federation claims that ship only endpoints for a transfinite-bounded or aperiodic rule system.

## 8. Bigraded Cohomology And KZ Diamonds

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/hacking/library/designation-grade/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/hacking/library/cohomological-degree/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/positing/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/docs/dev/journal/2026-05-25-shadows-and-apex-tower.md`

Invariant:

Bigraded settling cohomology has a designation axis and a cohomological-degree axis.
The CHL recursion focuses on first-order obstructions in truth-designated and inconsistency-designated components.
KZ-diamond 2-cells trivialize in strict/Scott-continuous regimes and remain non-trivial in transfinite-bounded/aperiodic regimes.

Implementation consequence:

Audit and federation cannot be reduced to scalar validity.
A future conformance suite needs hooks for regime-specific cohomology evidence, especially when asymmetric handedness or inconsistency sectors are part of a swarm claim.

## 9. SHP Is The Hypertext Packet Surface

Source:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/semantic-hypertext-packet/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/semantic-hypertext-packet/library/rfc-7992/docs/dev/journal/2026-05-24.md`
- `development/emsenn/active/hacking/spotcomp/HANDROLLED-SPOTCOMP-SPEC.html`
- `https://www.rfc-editor.org/rfc/rfc7992.html`

Invariant:

SHP is a semantic hypertext packet format where classes name morphism identities and `data-*` attributes carry carrier elements.
RFC 7992 structural classes are already SHP morphism identities for RFC-structured packets.
SHP is a sibling organ of SPOTCOMP, not a child of TRC or a generic document format.
RFC 7992 is an inhabitant profile for RFC-shaped SHP packets, not the whole SHP object.

Implementation consequence:

The SPOTCOMP spec proper should define SHP projections and packet conformance.
It should not define an alternate plain-text packet profile.
The `shp-profile` checker validates declarations for finite SHP packet objects, projection/markup directions, class-as-morphism identity, `data-*` carriers, RFC 7992 constraints, and no-script/no-required-external-resource safety.
It does not prove full HTML conformance or projection-morphism placement.

## 10. Modeled Players Need CGS

Source:

- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/code/structures/cgs.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/prime-event-structure/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/arena/hacking/library/strategy/hacking/library/concurrent-strategy/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/arena/hacking/library/strategy/hacking/library/innocent-strategy/docs/dev/journal/2026-05-26.md`

Invariant:

Modeled players are not just signed senders.
The repo's computing theory uses concurrent games with symmetry: objects are prime event structures with causality, conflict, polarity, and symmetry; morphisms are concurrent strategies on `A^perp || B`.
Sequential/innocent strategies are special cases.

Implementation consequence:

A SPOTCOMP swarm record must eventually expose player events, observation bounds, action bounds, handedness, strategy class, and symmetry/equivalence information.
The current player schema is a placeholder until that embedding is derived.

## 11. Chunk Chain Must Be Explicit

Source:

- `development/experimental/spotcomp/CHUNK-MAP.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/eavt/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/library/language/hacking/path-resolving/library/path-resolution/docs/dev/journal/2026-05-24.md`

Invariant:

SPOTCOMP is not obtained by jumping from settlement directly to a network protocol.
The repo forces a chunk chain: settlement becomes information only relative to receiver/context/provenance/aboutness; information becomes computable only when represented by executable and persistent substrate structures; computers become POSIX-shaped by a process/filesystem/userland contract; POSIX becomes SPOTCOMP through the path-theory CHL column and TRC; agents and games branch from computers and information respectively.

Implementation consequence:

Future implementation work must be organized by chunk boundary.
A runtime feature is normative only if its upstream chunk derivation is known or the gap is explicit.

## 12. Categorical Machinery Controls Code

Source:

- `development/experimental/spotcomp/CATEGORICAL-MACHINERY.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/tracing/library/trace/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/positing/hacking/library/positing-naturality/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration-2-category/hacking/closure-2-monad/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/library/local-settling/docs/dev/journal/2026-05-24.md`

Invariant:

The controlling order is categorical invariant, derivation obligation, conformance criterion, then code.
The current implementation probe tests a small row-level fragment and intentionally forgets several trace axes.
It cannot define SPOTCOMP.

Implementation consequence:

Every future code addition must declare which categorical obligation it probes.
If the code cannot represent the relevant trace axes, positing naturality, closure apex, regime data, local settling, or CGS mapping, it must remain a partial checker.

## 13. Path Typing Is A Conformance Surface

Source:

- `development/experimental/spotcomp/PATH-TYPING.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/path-category/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/library/language/hacking/path-resolving/library/path-resolution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`

Invariant:

Path identity, TRC co-location, dual filing, and generator variance are not conventions layered on top of SPOTCOMP.
They are part of the executable proof-tree surface.
A resource tree that cannot classify roles and prove schema/log/script and anchor discipline is not yet SPOTCOMP-shaped.

Implementation consequence:

The next conformance tooling should validate path-role declarations, dual filing, no authoritative `v` anchor, support-artifact non-authority, and projection provenance before it expands the swarm runtime.

## 14. Federation Must Declare Regime

Source:

- `development/experimental/spotcomp/REGIME-FEDERATION.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration-2-category/hacking/settling-endofunctor/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration-2-category/hacking/closure-2-monad/hacking/library/closure-merge-commutation/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/hacking/library/h1-top/docs/dev/journal/2026-05-26.md`

Invariant:

Federation is not just signed row transport.
Merge is safe as trace-increment evidence accumulation, but endpoint-state summaries are regime-dependent.
Strict and Scott-continuous regimes can justify endpoint summaries with the right proof witnesses.
Transfinite-bounded and aperiodic regimes can carry non-trivial orbit/cohomology invariants, so endpoint-only federation is insufficient.

Implementation consequence:

Federation envelopes or adjacent signed profiles must declare regime, payload kind, rule-system identity, frontier, and downgrade behavior.
Receivers must reject or downgrade payloads whose regime evidence they cannot verify, especially endpoint summaries in transfinite-bounded or aperiodic settings.

## 15. CGS Modeled-Player Profiles

Source:

- `development/experimental/spotcomp/CGS-EMBEDDING.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/code/structures/cgs.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/prime-event-structure/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/arena/hacking/library/strategy/hacking/library/concurrent-strategy/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/arena/hacking/library/strategy/hacking/library/innocent-strategy/docs/dev/journal/2026-05-26.md`

Invariant:

Modeled-player conformance must expose enough structure to be read as CGS-shaped: event identifiers, event kinds, Player/Opponent polarity, causality, minimal conflict, symmetry classes, and strategy declarations.
Prime-event-structure conflict is incompatible co-occurrence, not the same thing as a top or inconsistent settlement value.
Sequential/innocent behavior is a deterministic restriction of the concurrent strategy surface.

Implementation consequence:

The candidate `cgs-profile` checker validates declaration shape only: uniqueness, acyclic causality, conflict pair hygiene, strategy references, player-polarity action events, and sequential/innocent concurrency bounds.
It cannot decide full receptivity, innocence, interaction-and-hiding composition, or the symmetry quotient.
Those remain D9 obligations.

## 16. TRC/TDP Layout Is POSIX-To-SPOTCOMP Evidence

Source:

- `development/experimental/spotcomp/library/trc-tdp/specification.md`
- `development/experimental/spotcomp/TRC-LAYOUT.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/eavt/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/path-category/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/library/language/hacking/path-resolving/library/path-resolution/docs/dev/journal/2026-05-24.md`

Invariant:

TRC and TDP are one on-disk object read in two ways.
The TRC reading is the executable POSIX-to-SPOTCOMP memory contract: typed resources have co-located schema and trace-log witnesses, morphisms have script witnesses, path identity is categorical identity, package imports bind schema/script identities, admitted rows are dually filed at subject and predicate logs, and value-position indexes are secondary caches only.
The TDP reading is the same tree as the running theory derivation program: category is program, closure-rule sets execute by iteration to a least fixed point or declared non-final trajectory, and the trace is the execution log.

Implementation consequence:

The `trc-layout` checker validates declaration shape for co-location, imports, morphism monotonicity declarations, exact four-field EAVT rows, subject/predicate dual filing, and non-authoritative value indexes.
It intentionally does not inspect actual POSIX file modes, append flags, ESM default exports, behavioral monotonicity, schema-validation behavior, or full path hom-functor equality.

## 17. IETF Wire Profiles Are Boundary Bindings

Source:

- `development/experimental/spotcomp/WIRE-PROFILES.md`
- `development/experimental/spotcomp/IETF-CONFORMANCE.md`
- RFC 6838, RFC 6839, RFC 7464, RFC 8032, RFC 8259, RFC 8410, RFC 8785, RFC 9110, RFC 9457

Invariant:

IETF conformance attaches after the mathematical object boundary is fixed.
JSON syntax, canonicalization, media types, HTTP metadata, problem details, and Ed25519 signatures constrain wire representations; they do not define trace, settlement, SHP, modeled-player, CGS, or TRC semantics.

Implementation consequence:

The `wire-profile` checker validates declaration shape for representation kind, media type, required RFCs, canonicalization, signature profile, HTTP `Content-Type`, problem details, and unregistered SPOTCOMP-specific media type obligations.
It cannot replace actual media type registration, HTTP interoperability tests, TLS configuration, or cryptographic verification.

## 18. Agentic Embedding Grounds Modeled Players

Source:

- `development/experimental/spotcomp/AGENTIC-EMBEDDING.md`
- `lab/hacking/library/tech-extra/agentic-system/agentic-system.md`
- `lab/hacking/library/tech-extra/tool-use/tool-use.md`
- `lab/hacking/library/tech-extra/agent-memory/agent-memory.md`
- `lab/hacking/library/tech-extra/agent-orchestration/agent-orchestration.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/agentic-systems/agentic-systems.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/agentic-systems/library/character/character.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/agentic-systems/library/swarm/swarm.schema.json`

Invariant:

A SPOTCOMP modeled player must be grounded in computer-agent structure before it can be a proper swarm participant: environmental action through tools, goal-directed planning, persistent state, governance, skills as generator set, identity key, behavioral-space bound, sigma/delta commutation, and recognition-mediated swarm coordination.

Implementation consequence:

The `agentic-profile` checker validates declarations for systems, characters, skills, player bindings, and swarms.
It ensures agentic conditions are explicit and that swarm participants have modeled-player bindings.
It cannot prove the governance algebra, recognition-cell settlement, skill admissibility, behavioral-space inclusion, or CGS strategy correctness.

## 19. Information-To-Games Requires Observation Maps

Source:

- `development/experimental/spotcomp/INFORMATION-GAMES.md`
- `lab/hacking/library/being/doing/library/philosophy/semiotics/information/information.md`
- `lab/hacking/library/being/doing/library/library/information/knowing-as-settling/knowing-as-settling.md`
- `lab/hacking/library/being/doing/library/library/information/aboutness/aboutness.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/hacking/library/game-system/hacking/library/concurrent-game-system/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/arena/hacking/library/strategy/docs/dev/journal/2026-05-26.md`

Invariant:

The information-to-games branch is receiver-relative.
Information is not raw data; it is uncertainty reduction for a receiver.
Knowing is settled substrate state under admitted closure rules.
Aboutness is predication participation.
A modeled player can therefore enter CGS only through an observation map from settled information into the player's local view, not through a global synchronized state.

Implementation consequence:

The `information-game-profile` checker validates declarations for informational objects, observation maps, arena observation bindings, strategy bindings, and federation composition.
It rejects explicit global-frontier assumptions and strategy/player mismatches.
It does not prove the information-to-CGS functor, event-structure completeness, conflict inheritance, receptivity, innocence, or symmetry-groupoid laws.

## 20. Settling-To-Information Is Receiver-Relative

Source:

- `development/experimental/spotcomp/SETTLING-INFORMATION.md`
- `lab/hacking/library/being/doing/library/philosophy/semiotics/information/information.md`
- `lab/hacking/library/being/doing/library/library/information/knowing-as-settling/knowing-as-settling.md`
- `lab/hacking/library/being/doing/library/library/information/aboutness/aboutness.md`
- `lab/hacking/library/being/doing/library/philosophy/semiotics/document/document.md`
- `lab/archive/library/science/library/information/library/knowledge-systems/theories/predicated-knowledge-systems/concepts/discourse-community-as-fiber.md`
- `lab/archive/library/science/library/information/library/knowledge-systems/theories/predicated-knowledge-systems/concepts/epistemic-closure.md`
- `lab/archive/library/science/library/information/library/knowledge-systems/theories/predicated-knowledge-systems/code/structures/knowledge-fiber-algebra.md`
- `lab/archive/library/science/library/information/library/knowledge-systems/theories/predicated-knowledge-systems/code/structures/predicated-knowledge-system.md`

Invariant:

Settled trace data becomes information only relative to a receiver, discourse scope, question, closure-rule system, settlement frontier, provenance, and aboutness participation.
Documents are information-level preserved signs with purpose, provenance, and arrangement; they are not SPOTCOMP packet profiles.

Implementation consequence:

The `information-profile` checker validates declarations for scopes, receiver-relative informational artifacts, uncertainty reduction, aboutness participation, document provenance, aboutness closure links, and SHP projection bindings.
It cannot prove the category of informational artifacts, closure-rule correctness, complete aboutness closure, or SHP projection correctness.

## 21. Information-To-Computers Adds Witnesses

Source:

- `development/experimental/spotcomp/INFORMATION-COMPUTERS.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/eavt/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/tracing/library/trace/docs/dev/journal/2026-05-24.md`

Invariant:

The computer layer makes information executable and persistent by adding witnesses: schema as type/proposition/object, log as fiber evidence, script as closure-rule morphism, exact EAVT rows as transactionally located assertion carriers, canonical row identity for deterministic deduplication, and G-Set merge for federation.
These are witnesses for the information object; they are not replacements for it.

Implementation consequence:

The `information-computer-profile` checker validates declarations for source artifacts, computational resources, schema/log/script witnesses, exact EAVT carrier shape, append-only and canonical identity claims, content addressing, G-Set merge, and non-authoritative value indexes.
It cannot prove real validation, append-only behavior, script determinism, canonicalization correctness, or federation convergence.

## 22. Computers-To-POSIX Is An Operating-System Contract

Source:

- `development/experimental/spotcomp/COMPUTERS-POSIX.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/operating-system.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/doing/working/running/running.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/path-category/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`

Invariant:

POSIX is the reference operating-system surface where computer witnesses become inspectable and executable: one catalog root, categorical path identity, regular machine-readable files, LF-delimited logs, append behavior, userland process execution, stdio, signal forwarding, exit status, module loading, and explicit failure surfacing.

Implementation consequence:

The `posix-profile` checker validates declarations for path, file, append, process, and failure contracts.
It cannot inspect real filesystem state, enforce append flags, execute processes, validate byte encodings, or prove path hom-functor equality.

## 23. Governance Is Modal Restriction, Not A Policy Sidecar

Source:

- `development/experimental/spotcomp/GOVERNANCE.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/governance/assets/computing/platform/pypredcomp/docs/dev/decisions/authorization-is-modal-restriction.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/governance/assets/computing/platform/pypredcomp/docs/dev/specs/security/capability-model.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/governance/assets/computing/platform/pypredcomp/docs/dev/specs/filesystem/capability-permissions.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/governance/assets/computing/platform/pypredcomp/tests/conformance/test_modal_authz_box.py`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/governance/assets/computing/platform/pypredcomp/tests/conformance/test_t02_32f_observer_authoring.py`

Invariant:

Governance, capability checks, federation trust, session projection, authentication, and agent self-queueing are surfaces of one modal restriction operator over one accessibility relation.
Capability delegation is non-amplifying.
Denied side-effecting actions must not advance event logs or target fibers.
Revocation is trace growth, not historical deletion.

Implementation consequence:

The `governance-profile` checker validates declarations for the one-evaluator modal surface, exact EAVT authorization rows, non-amplifying delegation, revocation rows, action bounds, side-effect gates, and finite governance settlement projections.
It cannot prove modal restriction, capability-fiber implication, cache coherence, governance vote validity, or finite-settlement correctness.

## 24. Cohomology Audit Is Bigraded

Source:

- `development/experimental/spotcomp/COHOMOLOGY-AUDIT.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/hacking/library/designation-grade/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/hacking/library/cohomological-degree/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/hacking/library/h1-t/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/library/predication-fibration/library/predication-hyperdoctrine/hacking/library/bigraded-settling-cohomology/hacking/library/h1-top/docs/dev/journal/2026-05-26.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/prose/learning/claims/audit-content-via-inconsistency-sheaf-cohomology.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/theories/predicated-computing/code/structures/inconsistency-sheaf-record.md`

Invariant:

Swarm audit must distinguish truth-side and inconsistency-side cohomological content.
`H1_t` is the first truth-side obstruction; `H1_top` is the first inconsistency-side obstruction.
Audit-relevant contradictions, federation conflicts, and repair histories live in the inconsistency sheaf's cohomology, not in a scalar validity flag.

Implementation consequence:

The `cohomology-audit-profile` checker validates declarations for designation grades, cohomological degrees, `H1_t`, `H1_top`, inconsistency-sheaf records, optional FOUR/K4 projection sectors, and receiver downgrade policy.
It cannot compute cohomology, prove vanishing, derive top-cell membership, or validate cached cohomology values.

## 25. Trace Axes Are Not Row Fields

Source:

- `development/experimental/spotcomp/TRACE-AXES.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predication-cell/tracing/library/trace/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/trace-monoid/docs/dev/journal/2026-05-24.md`
- `development/active/hacking/proof-engine/cell-trace-shape.mjs`

Invariant:

The trace object has event, temporal/causal, evidence, recognition, categorical-refinement, and constitutive-provenance axes.
Exact EAVT rows are finite carrier rows for transactionally located assertions; they do not gain extra fields to smuggle in axes, and row interleaving does not by itself prove independence.
Constitutive provenance is accumulative and must be causally supported.

Implementation consequence:

The `trace-axis-profile` checker validates declaration shape for the rich trace object boundary: required axes, exact EAVT event rows, acyclic causal graph, direct causal support for provenance, irreflexive causally unordered trace-monoid independence, event-union join laws, and projection preservation/forgetting.
It cannot derive traces from positing, prove naturality under reindexing, or build the missing settlement functor.

## 26. Positing Is Least Extension, Rows Are Event Presentation

Source:

- `development/experimental/spotcomp/POSITING.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/positing.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/scripts/posit.mjs`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/hacking/library/positing-naturality/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/hacking/library/locution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/hacking/library/illocution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/settling/hacking/perlocuting/library/perlocution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/hacking/library/positing-entry/docs/dev/journal/2026-05-24.md`

Invariant:

Positing is the Scott-continuous, knowledge-order least-extension morphism on predication valuations.
It is natural under predicate-category reindexing, preserving datum `q` while changing cell location.
The active FOUR/articulation-cell implementation is a boolean specialization witness, not the general carrier.
Locution, illocution, and perlocution are distinct categorical positions: environmental decoding, pure event-bounded act, and closure/write propagation.

Implementation consequence:

The `positing-profile` checker validates declaration shape for the least-extension morphism, specialization-only active FOUR code, naturality generator actions, datum preservation, 2-cell status, speech-act factorization, exact EAVT event rows, and downstream effect boundaries.
It cannot prove naturality, implement general `L`, or derive the categorical-to-row bridge.

## 27. Predication Stages Are Regime-Categories

Source:

- `development/experimental/spotcomp/PREDICATION-STAGES.md`
- `development/active/articulating/articulating.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/predicating.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/positing.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/positing/settling/settling.schema.json`
- `development/active/hacking/tests/articulating-predicating.test.mjs`
- `development/active/hacking/tests/predication-category.test.mjs`

Invariant:

The foundational chain is a chain of predication categories, not just a list of verbs.
Articulating generates the aperiodic predication category.
Predicating generates the transfinite predication category.
Positing generates the Scott-continuous predication category.
Settling generates the finite predication category.
The direction is aperiodic to transfinite to Scott-continuous to finite; finite settlement and FOUR projections cannot define the upstream stages.

Implementation consequence:

The `predication-stage-profile` checker validates declaration shape for the four-stage mapping, downstream-only direction, finite-only FOUR placement, SHP as finite projection, and prelocutionary boundary preservation.
It cannot prove the functors between stage categories or derive transfinite predication generation beyond the active schema evidence.

## 28. Closure Settling Apex Controls Final Settlement

Source:

- `development/experimental/spotcomp/CLOSURE-SETTLING.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration-2-category/hacking/closure-2-monad/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration-2-category/hacking/settling-endofunctor/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/library/predication-fibration-2-category/hacking/closure-2-monad/hacking/library/closure-merge-commutation/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/perlocuting/library/perlocution/sigma-delta-cycle/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/perlocuting/library/perlocution/sigma-delta-cycle/delta-pass/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/perlocuting/library/perlocution/sigma-delta-cycle/sigma-pass/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/settling/hacking/library/local-settling/docs/dev/journal/2026-05-24.md`
- `development/active/hacking/proof-engine/settling-shape.mjs`

Invariant:

Closure is a lax-idempotent 2-monad on predication fibrations, with algebras exactly closed predication fibrations.
Settling is the closure-plus-increment orbit, and the settling apex is the Knaster-Tarski least fixed point.
The closure-merge commutation lemma reconciles close-then-merge and merge-then-close presentations.
Perlocution executes repeated `delta-pass -> sigma-pass`: delta accumulates evidence by knowledge join; sigma resolves contested cells through tensor updates.
Local settling is a bounded restriction of universal settling, including modeled-player state as one local case.

Implementation consequence:

The `closure-settling-profile` checker validates declaration shape for closure axioms, settling endofunctor evidence, closure-merge bridge, apex/fixed-point claims, sigma/delta roles, local-settling restriction, bounded-fuel partiality, and finite-only FOUR placement.
It cannot compute closure, prove Knaster-Tarski, prove the full 2-categorical lift, or decide closure ordinals.
A runtime that stops after bounded rule execution must report a partial prefix unless it carries fixed-point evidence.

## 29. CHL Language Cones Separate Column Morphisms

Source:

- `development/experimental/spotcomp/CHL-LANGUAGE-CONES.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/library/language/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/library/language/hacking/path-resolving/library/path-resolution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/agents/hacking/library/claude/hacking/library/claude-code/inferring/hacking/parsing/hacking/detecting/hacking/library/styling-pattern/hacking/library/idiom/hacking/library/by-chl-language-cones/hacking/library/type-as-proposition-as-object/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/agents/hacking/library/claude/hacking/library/claude-code/inferring/hacking/parsing/hacking/detecting/hacking/library/styling-pattern/hacking/library/idiom/hacking/library/by-chl-language-cones/hacking/library/term-as-proof-as-morphism/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/agents/hacking/library/claude/hacking/library/claude-code/inferring/hacking/parsing/hacking/detecting/hacking/library/styling-pattern/hacking/library/idiom/hacking/library/by-chl-language-cones/hacking/library/function-type-as-implication-as-exponential/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/agents/hacking/library/claude/hacking/library/claude-code/inferring/hacking/parsing/hacking/detecting/hacking/library/styling-pattern/hacking/library/idiom/hacking/library/by-chl-language-cones/hacking/library/categorical-model-as-cone-apex/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/docs/dev/journal/2026-05-25-shadows-and-apex-tower.md`

Invariant:

A CHL language is an open-ended categorical apex with column-leg functors into type, proof, category, domain, path, and fiber-stable columns.
Classical type/proof/morphism identification is a specialization.
In the non-degenerate reading, column morphisms are distinct categorical inhabitants until a theorem proves scoped coincidence.
SPOTCOMP's path-theory column is real because Yoneda on the POSIX path category makes path identity categorical.

Implementation consequence:

The `chl-language-profile` checker validates declarations for the language apex, required column legs, distinct SPOTCOMP morphism inventory, scoped coincidence policy, path-theory obligations, and pure-morphism/wrapper boundary.
It cannot prove the coincidence theorem, derive the path-theory cone-leg, or prove Yoneda.
A runtime command may compose morphisms, but it must name the composition rather than becoming an untyped primitive.

## 30. Predication Fiber Algebra Generalizes The Value Substrate

Source:

- `development/experimental/spotcomp/PREDICATION-FIBER-ALGEBRA.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/library/predication-fibration/library/predication-fiber-algebra/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/library/predication-fibration/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/library/predication-fibration/library/predication-hyperdoctrine/docs/dev/journal/2026-05-24.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/predication-fiber-algebra.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/predication-fibration.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/predication-hyperdoctrine.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/prose/learning/claims/twist-product-residuation.md`
- `/predication-categories/library/predication-cell-complex-site/content/explanations/exhaustiveness-of-four-predication-cell-complex-site-generators.md`

Invariant:

The local value substrate is the uniform predication fiber algebra `A_p = (L x L)^(E x E)`, with positive and negative evidence components and pointwise bilattice/residuated operations.
The predication fibration packages these fibers over the predicate category by A1-A3, and the hyperdoctrine layer adds property-like two-order adjoints, Frobenius for both meets, Beck-Chevalley, and dual comprehension.
FOUR is the boolean specialization of this machinery, and classical relations are a further collapse.

Implementation consequence:

The `predication-fiber-profile` checker validates declarations for the general fiber algebra, fibration, hyperdoctrine, FOUR boundary, and implementation rules that reject undeclared carriers.
It cannot prove twist-product residuation, predicate-generator exhaustiveness, Beck-Chevalley, Frobenius, or comprehension.
Any runtime that only checks FOUR values is a finite-specialization checker, not a SPOTCOMP value checker.

## 31. Modeled Players Are Not Character Records Or Peer Keys

Source:

- `development/experimental/spotcomp/PLAYER-CHARACTER-BOUNDARY.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/spotcomp/settling/library/player/player.schema.json`
- `lab/archive/multi-user-dungeon/tab/docs/2026-03-11/agent-hierarchy.md`
- `lab/archive/doing/working/hacking/doing/working/planning/library/task/library/characters-as-cells/characters-as-cells.md`
- `lab/archive/old-archive/triage/engineering-archive/library/humanities/theories/philosophy/theories/relating/triage/provenance/relating-archive/sscu-sprint/docs/math/structure/agent.md`
- `lab/archive/old-archive/triage/engineering-archive/library/humanities/theories/philosophy/theories/relating/triage/provenance/relating-archive/sscu-sprint/domains/universes/semiotic-universe/domains/interactive-semioverse/domains/agential-semioverse/agential-semioverse.md`
- `lab/archive/old-archive/triage/engineering-archive/library/humanities/theories/philosophy/theories/relating/triage/provenance/relating-archive/sscu-sprint/domains/universes/semiotic-universe/domains/interactive-semioverse/domains/agential-semioverse/domains/computing/agential-semioverse-repository/theory/agent-skill-interaction.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/teaching/teaching.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/code/structures/cgs.md`

Invariant:

The external player, system-held modeled player, character, persona, role, skill, method/tool surface, and CGS strategy are distinct positions.
A character is one kind of player target, but a modeled player is the system's local-settling model of an external entity.
Persona scopes roles; roles bundle skills; skills denote admissible monotone operators; method/tool surfaces execute beneath skills.
Teaching a skill to a character is substrate-side predication on the bearer record; host installation and player binding are downstream and distinct.

Implementation consequence:

The `player-character-profile` checker validates this boundary before a swarm can use a player record as modeled-player evidence.
Key, inbox, and outbox fields are insufficient by themselves.
The declaration must name external/model distinction, local settling, character/persona/role/skill surfaces when relevant, governance and capability bounds, handedness, observation/action boundaries, and CGS strategy binding.
The checker does not prove local-settling correctness, skill admissibility, modal governance, host installation correctness, CGS receptivity, or strategy composition.

## 32. Generator Variance Determines Codomain Shape

Source:

- `development/experimental/spotcomp/GENERATOR-VARIANCE.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/hacking/extending/extending.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/specializing/specializing.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/prose/remarks/specialization-as-open-immersion.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/docs/dev/journal/2026-05-27.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/settling/sampling-a-predication-cell/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predication-cell/slicing-to-predication-cell-trace/docs/dev/journal/2026-05-27.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/settling/assembling-from-predication-settling/docs/dev/journal/2026-05-27.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/settling/hacking/library/local-settling/docs/dev/journal/2026-05-24.md`

Invariant:

Generator variance is a proof obligation on a generator position.
Extension requires a structure-preserving embedding of the domain into a codomain that admits additional structure.
Restriction selects a subcategory, subfiber, subobject, finite frontier, trace slice, local settling, or certified projection and must declare what it forgets.
Coincidence cites a scoped theorem without collapsing morphism positions outside the theorem scope.
Unknown variance blocks strong conformance.

Implementation consequence:

The `generator-variance-profile` checker validates declaration shape for these obligations and requires local examples: product-position enumeration and cell sampling as extensions; cell-trace slicing, assembling from predication settling, and local settling as restrictions.
It cannot prove the embeddings, restrictions, or coincidence theorems.
Its purpose is to stop a runtime or path checker from treating an undocumented variance choice as conformance evidence.

## 33. Prelocutionary Ingress Preserves Stage Categories

Source:

- `development/experimental/spotcomp/PRELOCUTIONARY-INGRESS.md`
- `development/active/library/utterance/docs/dev/journal/2026-05-25.md`
- `development/active/library/token/docs/dev/journal/2026-05-25.md`
- `development/active/library/claim/docs/dev/journal/2026-05-25.md`
- `development/active/articulating/articulating.schema.json`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/hacking/library/locution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/settling/hacking/illocuting/library/illocution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/settling/hacking/perlocuting/library/perlocution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/hacking/library/positing-entry/docs/dev/journal/2026-05-24.md`

Invariant:

External trigger bytes are not trace evidence and not an utterance by themselves.
The primitive ingress carrier for articulating is the ordered pair of token and claim; both are non-assembling primitives, and their string representation is only finite presentation.
Articulating maps utterance to the aperiodic predication category.
Locution decodes environmental shapes into typed internal input; illocution is pure event-bounded positing; perlocution is closure propagation.
A handler that parses, posits, writes, and closes in one proof object collapses distinct categorical positions.

Implementation consequence:

The `prelocutionary-ingress-profile` checker validates declaration shape for token/claim/utterance grounding, articulating ingress, locutionary handler classes, parse-before-illocution behavior, and implementation boundaries that keep transport parsing distinct from positing and closure evidence.
It cannot prove token-before-claim ordering, articulating category generation, or real handler correctness.

## 34. Canonical Identity Binds Rows To IETF Bytes

Source:

- `development/experimental/spotcomp/CANONICAL-IDENTITY.md`
- RFC 8259
- RFC 7493
- RFC 8785
- RFC 7464
- RFC 3339
- RFC 8032
- `development/experimental/spotcomp/src/trace.mjs`
- `development/experimental/spotcomp/src/envelope.mjs`

Invariant:

SPOTCOMP row identity is `sha256(jcs(row))` over the exact EAVT row.
It is not line position, arrival order, local object identity, or file byte offset.
JCS brings I-JSON preconditions: duplicate object names are rejected, Unicode strings are preserved without normalization, JSON numbers stay inside the interoperable boundary or move to strings, object properties sort recursively, and arrays keep their order.
A post-parse object cannot prove duplicate-name absence if the parser silently discarded duplicates.

Implementation consequence:

The `canonical-identity-profile` checker validates declaration shape for row IDs, JSON/JCS/I-JSON preconditions, Ed25519 signature input, JSON text sequence item identity, and timestamp policy.
It explicitly records that the current local `canonicalJson` probe is not a complete RFC 8785 implementation and that strong imports need a duplicate-detecting parser.
Signed RFC 7464 streams must bind item canonical bytes or a row-ID manifest because the sequence itself has no canonical JSON form.

## 35. Recognition Gates Admission, Not Row Presence

Source:

- `development/experimental/spotcomp/RECOGNITION.md`
- `development/experimental/spotcomp/TRACE-AXES.md`
- `development/experimental/spotcomp/AGENTIC-EMBEDDING.md`
- `development/experimental/spotcomp/INFORMATION-GAMES.md`
- `development/experimental/spotcomp/CGS-EMBEDDING.md`
- `development/active/proof-engine/predication-cell-trace-shape.mjs`
- `development/active/proof-engine/finite-predication-cell-trace-shape.mjs`
- `development/active/proof-engine/finite-predication-trace-family-shape.mjs`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/hacking/learning/hacking/answering/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/hacking/library/illocution/docs/dev/journal/2026-05-24.md`

Invariant:

Recognition is a trace axis and receiver-relative admission discipline.
Finite shape recognition checks carrier shape and local laws, such as monotonicity or provenance accumulativity; it does not by itself settle recognition.
Row presence, parse success, signature verification, and schema success are each necessary in their own contexts, but none is sufficient to admit evidence into a receiver's local settlement or game play.
Swarm roles are recognized through recognition cells and governance, not out-of-band flags.

Implementation consequence:

The `recognition-profile` checker validates declaration shape for recognition fiber preservation, shape-recognition limits, admission gates, swarm role derivation, and CGS admission boundaries.
It blocks strong swarm conformance when recognition is unknown, while allowing rejected or quarantined evidence to become local audit/conflict material.
It cannot prove recognition-cell settlement, the information-to-CGS functor, modal governance, or strategy laws.

## 36. CGS Strategy Laws Are Morphism-Level Obligations

Source:

- `development/experimental/spotcomp/CGS-STRATEGY-LAWS.md`
- `development/experimental/spotcomp/CGS-EMBEDDING.md`
- `development/experimental/spotcomp/MODELED-PLAYERS.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/prime-event-structure/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/arena/hacking/library/strategy/hacking/library/concurrent-strategy/docs/dev/journal/2026-05-26.md`
- `development/active/articulating/library/aperiodic-predication-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predication-cell/hacking/library/event/hacking/library/event-structure/hacking/library/arena/hacking/library/strategy/hacking/library/innocent-strategy/docs/dev/journal/2026-05-26.md`
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/code/structures/cgs.md`

Invariant:

CGS conformance is not only event structure.
A CGS morphism `A -> B` is a concurrent strategy on `A^perp || B`, quotient-read under the symmetry groupoid.
It must be receptive to Opponent extensions and preserve causality and conflict.
Composition is strategy interaction with intermediate moves hidden, associative up to canonical isomorphism.
Sequential and innocent strategies are restrictions of the concurrent strategy surface; they cannot define the general swarm model.

Implementation consequence:

The `cgs-strategy-laws-profile` checker validates declaration shape for CGS object boundaries, morphism arena shape, receptivity, symmetry quotienting, interaction-and-hiding composition, and sequential/innocent restrictions.
It rejects key identity, trace-loop equality, or handler equality as strategy equivalence evidence.
It cannot prove receptivity, composition, quotient correctness, innocence, full abstraction, or final modeled-player embedding.

## 37. Bigraded Diamond Swarms Are The Swarm Mathematics Boundary

Source:

- `development/experimental/spotcomp/BIGRADED-DIAMOND-SWARMS.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/kz-diamond-strict-commutation.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/narratives/two-disentangled-kz-structures.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/bigraded-common-knowledge.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/bigraded-settling-cohomology.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/prose/learning/claims/bigraded-aperiodic-regime-trichotomy.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/prose/learning/claims/bigraded-realizability-refinement.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/objects/multi-observer-system.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/network-sheaf-consensus-on-agent-graphs.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/crdt-convergence-with-per-observer-rules.md`

Invariant:

The swarm-relevant diamond is the strict commutation of closure KZ and fibration KZ axes.
Closure acts on values; fibration refinement acts on cleavage and indexing.
The epistemic layer is bigraded: truth-axis and knowledge-axis common knowledge are distinct fixed-point operators.
The cohomology layer is also bigraded, with truth and inconsistency rows and an aperiodic trichotomy.
Swarms enter through multi-observer systems `V : O -> Settlings_B`, with agent graphs as observer categories and per-observer rule systems allowed.

Implementation consequence:

The `bigraded-diamond-swarm-profile` checker validates declaration shape for KZ diamond axes, bigraded common knowledge, bigraded cohomology, multi-observer swarms, aperiodic tiling witnesses, and the DRIP/Remote ID boundary for UAS deployments.
It blocks strong modeled-player swarm conformance when a profile collapses truth/knowledge axes, treats keys as modeled players, treats peer count as aperiodicity, or claims tiling satisfies drone standards without the applicable DRIP layer.
It does not prove the KZ diamond, compute cohomology, derive concrete tilings, or validate live standards exchanges.

## 38. Aperiodic Swarm Witnesses Need Substitution And MLD Evidence

Source:

- `development/experimental/spotcomp/APERIODIC-SWARM-WITNESS.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/anderson-putnam-direct-limit.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/aperiodic-classifying-invariant.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/aperiodic-co-classifying-invariant.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/step-n-substitution-rule.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/step-n-classifying-invariant.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/concepts/mutually-locally-derivable.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/aperiodic-regime-classification.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/examples/benchmark-2-thue-morse.md`

Invariant:

Aperiodic swarm structure is a settling-classification claim.
The witness must name local-settling tiles, finite approximants, transition maps, direct-limit cohomology, classifying invariant, MLD comparison scope, and substitution matrix status when a step-n substitution is claimed.
Bilattice cardinality coincidence does not prove structural alignment; an alignment claim needs a named bilattice operation and a commutation witness.
Singular substitutions and unstable weights downgrade generic rank claims.

Implementation consequence:

The `aperiodic-swarm-witness-profile` checker validates declaration shape for local-settling tiles, substitution matrices, direct-limit witnesses, MLD criteria, bigraded invariant slots, bilattice-alignment evidence, and weighted-swarm downgrade policy.
It blocks strong aperiodic swarm conformance when a profile relies on peer count, graph topology, clock behavior, bare alphabet size, or hidden protocol weights.

## 39. DRIP/UAS Binding Is A Standards Layer, Not Swarm Mathematics

Source:

- `development/experimental/spotcomp/DRIP-UAS-BINDING.md`
- `https://datatracker.ietf.org/wg/drip/documents/`
- `https://www.rfc-editor.org/rfc/rfc9153`
- `https://www.rfc-editor.org/rfc/rfc9374`
- `https://www.rfc-editor.org/rfc/rfc9434`
- `https://www.rfc-editor.org/rfc/rfc9575`
- `https://www.rfc-editor.org/rfc/rfc9886`

Invariant:

As of 2026-05-28, the IETF DRIP working-group page lists five RFCs: requirements/terminology, DET identity, architecture, broadcast authentication, and DETs in DNS.
These standards constrain UAS Remote ID identity, authentication, registry, DNS/DIME lookup, and observer-facing trust evidence.
They do not prove SPOTCOMP modeled-player identity, CGS strategy laws, bigraded common knowledge, or aperiodic tiling.

Implementation consequence:

The `drip-uas-profile` checker validates declaration shape for the five-RFC inventory, DET/UAS ID mapping, broadcast RID authentication, DNS/DIME registry lookup, and local SPOTCOMP admission after standards checks.
It keeps active Internet-Drafts non-normative and blocks UAS conformance claims that infer DRIP compliance from tiling, local row identity, or modeled-player records.

## 40. Moduli Descent And Laplacian Machinery Refine Swarm Claims

Source:

- `development/experimental/spotcomp/MODULI-DESCENT-LAPLACIAN.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/meta-moduli-stack-theorem.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/meta-stratification-by-regime.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/regime-decomposition.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/narratives/d-frame-cohomology-framework.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/narratives/cellular-extension-plan.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/verdier-duality-bitopological-site.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/q-enriched-sheaf-direct-inverse-image.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/strong-mld-via-composed-duality.md`

Invariant:

Closure-rule systems live in a meta-moduli stack whose invariant is closure-equivalence and effective descent of closure operators.
Regime labels are two-level: actual settling regime and maximum attainable rule-system meta-regime.
Named substitutions are regime-sensitive examples rather than interchangeable aperiodic tokens: Padovan is finite/strict placement, Fibonacci is Scott-continuous placement, and Tribonacci is transfinite placement.
D-frame cohomology uses the Tarski/Lawvere Laplacian route; Verdier duality supplies sheaf/cosheaf presentations and composes with bilattice negation.
Strong MLD adds firing-orbit type data to ordinary MLD.

Implementation consequence:

The `moduli-descent-laplacian-profile` checker validates declaration shape for meta-moduli descent, settling-vs-meta regime declarations, regime-sensitive named examples, Q-enriched Laplacian scope, Verdier/six-functor scope, and strong-MLD firing-orbit data.
It blocks strong conformance claims that identify rule systems by text alone, infer meta-regime from one run, flatten d-frame cohomology to a single slot, or treat ordinary MLD as strong MLD.

## 41. Regime Substitution Ladder Separates Placement From Benchmark Lifts

Source:

- `development/experimental/spotcomp/REGIME-SUBSTITUTION-LADDER.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/step-n-substitution-rule.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/objects/step-n-moduli-substack.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/examples/benchmark-1-fibonacci.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/examples/benchmark-3-padovan.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/examples/benchmark-suite-summary.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/step-n-and-bilattice-correspondence.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/canonical-step-shift-resolution.md`

Invariant:

The lab benchmark convention can lift named substitutions over `E = omega_1` and classify the benchmark run as aperiodic.
SPOTCOMP staged placement is a separate axis: Padovan is finite/strict placement, Fibonacci is Scott-continuous placement, and Tribonacci is transfinite placement.
Step-n moduli membership records arity and substitution-matrix family but does not decide staged placement.
Bilattice cardinality coincidence at n = 2, 3, and 4 does not become structural alignment without operation-level commutation evidence.

Implementation consequence:

The `regime-substitution-ladder-profile` checker validates declaration shape for the named placement ladder, benchmark-lift boundary, step-n/bilattice boundary, and implementation downgrade policy.
It blocks strong conformance claims that use substitution names, alphabet size, step depth, or benchmark suite regime as a complete regime classifier.

## 42. Realizability And Deformation Control Realized Swarm Claims

Source:

- `development/experimental/spotcomp/REALIZABILITY-DEFORMATION.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/meta-realizability-map.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/narratives/realizability-program.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/realizability-cardinality-bound.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/c-naturality-coupling-realizability-refinement.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/tangent-dimension-constructible-non-semicontinuous.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/regime-stratification-non-semicontinuity.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/chl-recursion-stabilization-check.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/meta-moduli-deformation-theory.md`

Invariant:

The meta-realizability map sends settling classes to closure-equivalence classes of generating rule systems and has increment-sequence fibers.
Actual settling regime is bounded above by the rule system's meta-regime.
Realizable classes are controlled by regime, bigraded value type, predicate-naturality, and rule-language fragment.
Predicate-generator morphisms couple firing patterns across predicates.
Tangent dimension is `Ext^1`, agrees with `H1` in the settling-associated sheaf scope, and is constructible but not semicontinuous along knowledge-order enhancement.
CHL stabilization is a tangent comparison through the derivative of `pi^real`.

Implementation consequence:

The `realizability-deformation-profile` checker validates declaration shape for stack-morphism identity, increment fibers, realizability axes, predicate-naturality coupling, deformation tangent data, CHL-stabilization scope, and downgrade policy.
It blocks strong conformance claims that infer realizability from one run, identify meta-points by rule text, ignore predicate coupling, or use monotone trace growth as a semicontinuity theorem.

## 43. Void Cone Material Translates To Stage Relationlessness

Source:

- `development/experimental/spotcomp/VOID-RELATIONLESSNESS-STAGES.md`
- `development/active/library/void/void.schema.json`
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/potential-aperiodic-predication-cell.schema.json`
- `development/active/library/utterance/docs/dev/journal/2026-05-25.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/void-cone-cohomology.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/void-cone-associated-graded-direct.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/value-agnostic-void-cone.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/narratives/void-cone-structure.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/narratives/geometries-of-failure-dynamics-of-void.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/lorentzian-apex-void-as-timelike-spacelike.md`
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/theorems/tropical-rank-collapse-classification.md`

Invariant:

The old void-cone vocabulary is not discarded, but it is read through the current four stage categories.
Void is the null relationless case at articulating, witnessed finitely as JSON `null` and as both slots of the potential aperiodic predication cell.
Void filtration descends by stage; its associated graded pairs with apex `H1`, while `V_infty` remains a separate permanent-relationlessness invariant.
The construction is value-agnostic and includes bilattice, stochastic, Lawvere, and Lorentzian null cases.
Failure geometry means obstruction geometry of staged predication, not runtime failure.

Implementation consequence:

The `void-relationlessness-profile` checker validates declaration shape for stage translation, null relationlessness, void filtration, apex pairing, value-agnostic instances, failure-geometry scope, and weighted rank-collapse boundaries.
It blocks strong conformance claims that treat void as exception handling, finite FOUR-only ontology, or continuous rank preservation without a shape-specific stability cone.

## 44. Trace Monoid Histories Need A Settlement Action

Source:

- `development/experimental/spotcomp/TRACE-MONOID-SETTLEMENT.md`
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/library/scott-continuous-posit-category/settling/hacking/trace-monoid/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/hacking/library/positing-naturality/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/library/predication-fibration-2-category/hacking/closure-2-monad/hacking/library/closure-merge-commutation/docs/dev/journal/2026-05-24.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/lean/PredicationCategories/Homebrew/Settling/CRDT.lean`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/prose/learning/claims/settling-merge-semilattice.md`
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/prose/learning/claims/modeling-preorder-independence.md`

Invariant:

The trace monoid `M(Sigma, I)` represents finite staged histories modulo declared independent swaps.
Its prefix order is a history category, and Foata normal form gives block-depth evidence.
The bridge to settlement is an action from stage-typed steps to atomic or batch positings on predication valuations.
Closure-driven convergence is backed by closure-merge commutation and the CRDT theorem: closed initial state plus common closure operator plus same multiset of writes yields the same final state regardless of write order.
Knowledge-order merge and truth-order modeling remain independent.

Implementation consequence:

The `trace-monoid-settlement-profile` checker validates declaration shape for history construction, independence evidence, valuation action, same-trace-class valuation equality, CRDT convergence conditions, Foata/prefix summaries, and federation downgrades.
It blocks claims that row order, peer difference, or G-Set merge alone proves mathematical independence or settlement equivalence.

## 45. SPOTCOMP Means Subject-Predicate-Object Trace Computer Operating Modeled-Players

Source:

- user correction in this session;
- `development/experimental/spotcomp/MODELED-PLAYER-SWARM-DYNAMICS.md`;
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/object/library/thing/library/category/hacking/library/computing/spotcomp/settling/library/player/player.schema.json`;
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/structures/multi-observer-system-with-rules.md`;
- `lab/archive/library/humanities/library/math/library/categories/theories/predication-theory/code/transformers/agentive-positing-morphism.md`;
- `lab/archive/relating-repo/relating-repo/library/theories/humanities/theories/math/theories/categories/theories/predication-categories/narratives/tunneling-and-agential-dynamics.md`;
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/hacking/library/ludics/docs/dev/journal/2026-05-24.md`.

Invariant:

SPOTCOMP is not a trace-only name.
It expands as Subject-Predicate-Object Trace Computer Operating Modeled-Players.
The specification family must therefore derive the subject/predicate/object predication theory, trace substrate, computer substrate, operating mode, modeled-player semantics, CGS strategy theory, and ludic/game-theoretic machinery.
The active ludics note places ludics as a paraconsistent linear-logic category on the predication-fiber substrate, sibling to CGS rather than a finite settlement stage.

Implementation consequence:

The `modeled-player-swarm-dynamics-profile` checker records the next modeled player boundary, but it is only a declaration probe.
The next missing surface is continuous learning: learning must be specified as monotone, governed, trace-bearing change in modeled-player settlings/rule systems/skills, not as untracked runtime adaptation.

## 46. Continuous Learning Is Modeled-Player Trajectory Evidence

Source:

- user correction in this session;
- `development/experimental/spotcomp/CONTINUOUS-LEARNING.md`;
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/hacking/learning/hacking/answering/docs/dev/journal/2026-05-24.md`;
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/positing/hacking/learning/hacking/teaching/hacking/referencing/docs/dev/journal/2026-05-24.md`;
- `lab/hacking/articulating/library/stable-articulation-cell/predicating/hacking/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/teaching/teaching.md`;
- `lab/archive/old-archive/triage/engineering-archive/library/humanities/theories/philosophy/theories/relating/triage/provenance/relating-archive/sscu-sprint/domains/universes/semiotic-universe/domains/interactive-semioverse/domains/agential-semioverse/agential-semioverse.md`;
- `lab/archive/old-archive/triage/engineering-archive/library/humanities/theories/philosophy/theories/relating/triage/provenance/relating-archive/sscu-sprint/domains/universes/semiotic-universe/domains/interactive-semioverse/domains/agential-semioverse/domains/computing/agential-semioverse-repository/theory/agent-skill-interaction.md`;
- `development/active/articulating/library/aperiodic-articulation-category/library/aperiodic-predication-cell/library/potential-aperiodic-predication-cell/predicating/library/transfinite-predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/hacking/library/ludics/docs/dev/journal/2026-05-24.md`.

Invariant:

Continuous learning in SPOTCOMP is monotone governed change in modeled-player representation.
Answering and referencing form the learn/use loop: projection from predication-cell-set, positing into `Phi = E x Pi x E`, closure/settle, then later projection from the updated settling.
Teaching is bearer-side predication, not mutation of the conferred object.
Skill improvement is a closure operation.
Memory is a local fragment.
Rule learning changes `r(o)` and is a transition unless closure equivalence is proved.

Implementation consequence:

The `continuous-learning-profile` checker records declaration evidence for these distinctions and rejects shortcuts: hidden weight updates, prompt context presence, skill installation, and rule changes without transition records do not count as strong learning evidence.
