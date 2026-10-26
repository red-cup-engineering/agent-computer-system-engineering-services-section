# Derivation Chunk Map

Status: source-backed sketch.
This map records the large dependency chunks SPOTCOMP must derive before the specification can be final.
It is not a replacement for proofs.

The user-specified chunk chain is:

`settling -> information -> computers -> POSIX -> SPOTCOMP`

with two sibling derivations:

- `computers -> agents`
- `information -> games`

## 1. Settling To Information

Sources:

- `lab/hacking/library/being/doing/library/library/information/knowing-as-settling/knowing-as-settling.md`
- `lab/hacking/library/being/doing/library/philosophy/semiotics/information/information.md`
- `lab/hacking/library/being/doing/library/philosophy/semiotics/document/document.md`
- `lab/hacking/library/being/doing/library/library/information/aboutness/aboutness.md`

Current picture:

Settling gives the substrate state of what a community knows under its closure-rule system.
Information is not raw data; it is a difference registered by a receiver and capable of changing that receiver's state.
A document is a preserved sign whose provenance and arrangement matter because they shape what can be reconstructed or proved.
Aboutness is not out-of-band metadata; it is participation in predications involving the entity.

SPOTCOMP consequence:

The information layer should be derived as receiver-relative settlement and predication participation.
It must not be reduced to file formats or human prose artifacts.
Finite artifacts are informative only through the settled trace frontier and the receiver context that can register them.

Open obligation:

Define the category whose objects are settled informational artifacts and whose morphisms preserve receiver-relative uncertainty reduction, provenance, and aboutness closure.

Current working surface: [SETTLING-INFORMATION.md](./SETTLING-INFORMATION.md), [schema/information-profile.schema.json](./schema/information-profile.schema.json), and [src/information-profile.mjs](./src/information-profile.mjs) check declaration-level preconditions for that category.

## 2. Information To Computers

Sources:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/eavt/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/typed-resource-catalog.schema.json`

Current picture:

At the computer-operating-system layer, EAVT is a substrate row-format for one transactionally located assertion.
It is the row-format mathematical objects take when persisted in a row-oriented serialization.
The TRC/TDP specification describes SPOTCOMP's on-disk proof tree: every typed resource has a schema as type/proposition/object, a per-thing JSONL log as the fiber's inhabiting evidence, and, for morphisms, a script as the knowledge-monotone closure rule.
The TRC reading is catalog/memory; the TDP reading is running theory derivation program.

SPOTCOMP consequence:

The computer layer is where settled information becomes executable and persistent: schemas validate admissible terms, logs accumulate trace evidence, scripts fire closure rules, and canonical bytes/content addresses support deterministic federation.
EAVT is a computer-operating-system carrier for trace events; it is not itself the whole mathematical object.

Open obligation:

Derive why the computer substrate should use this exact four-field row carrier, canonical byte identity, and schema/log/script triad from information-layer requirements rather than only from historical Datomic/SPOTCOMP practice.

Current working surface: [INFORMATION-COMPUTERS.md](./INFORMATION-COMPUTERS.md), [schema/information-computer-profile.schema.json](./schema/information-computer-profile.schema.json), and [src/information-computer-profile.mjs](./src/information-computer-profile.mjs) check declaration-level witnesses for the information-to-computer bridge.

## 3. Computers To POSIX

Sources:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/operating-system.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/doing/working/running/running.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/path-category/docs/dev/journal/2026-05-24.md`

Current picture:

An operating system is a system whose running supervises subsystems and exposes a userland surface.
The computer-operating-system running schema extends that with POSIX-shaped operational cells: binding stdio, forwarding signals, stopping, spawning, dispatching, and exiting by status code.
The path category then gives POSIX paths categorical structure: root initial object, paths as objects, ancestor-to-descendant containment as morphisms.

SPOTCOMP consequence:

POSIX is not merely a storage backend.
It is the concrete path category and process/userland surface through which the computer substrate becomes inspectable and executable.

Open obligation:

Specify exactly which POSIX properties SPOTCOMP requires: path syntax, regular files, LF-delimited text, process execution, stdio, exit status, signals, atomic append assumptions, and filesystem failure behavior.

Current working surface: [COMPUTERS-POSIX.md](./COMPUTERS-POSIX.md), [schema/posix-profile.schema.json](./schema/posix-profile.schema.json), and [src/posix-profile.mjs](./src/posix-profile.mjs) check declaration-level POSIX contract surfaces for paths, files, append, process execution, and failure handling.

## 4. POSIX To SPOTCOMP

Sources:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/path-category/path-category.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/library/language/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/library/category/library/language/hacking/path-resolving/library/path-resolution/docs/dev/journal/2026-05-24.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`

Current picture:

SPOTCOMP contributes a path-theory column to CHL via Yoneda on the POSIX path category.
The on-disk path is categorical identity, not a naming convention.
TRC/TDP then realizes this as a catalog/program discipline: per-thing paths, schema/log/script co-location, closure-rule execution, dual filing at subject and predicate anchors, append-only log semantics, and G-Set federation.

SPOTCOMP consequence:

The POSIX-to-SPOTCOMP derivation is what makes the active tree executable and auditable.
Editing a typed path is a CHL operation projected into the path-theory column.
A SPOTCOMP implementation must preserve this identity discipline or it is no longer implementing the same mathematical object.

Open obligation:

Write a path-typing and TRC-conformance checker that proves path roles, schema/log/script co-location, dual filing, no authoritative `v` anchor, canonical row identity, and deterministic projection.

## 5. Computers To Agents

Sources:

- `lab/hacking/library/tech-extra/agentic-system/agentic-system.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/agentic-systems/agentic-systems.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/agentic-systems/library/character/character.schema.json`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/agentic-systems/library/swarm/swarm.schema.json`

Current picture:

An agentic system is a computational system with environmental action, goal-directed multi-step planning, and persistent state.
The active schema for agentic systems adds a member set, governance process, governing soul, and community acts.
Character records carry agent kind, governance regime, skill generators, identity key, behavioral-space bound, and sigma/delta commutation flags.
Swarm records are parallel character collections coordinating through a shared cell graph under recognition discipline.

SPOTCOMP consequence:

Agents are not just peers with keys.
They are computer-realized systems with tool surfaces, persistent trace state, governance, skills as generators, and recognition-mediated roles.
A SPOTCOMP swarm implementation must represent those as trace-governed, auditable structures.

Open obligation:

Derive the exact embedding from computer-operating-system actions into agentic-system character/swarm records, and then into the modeled-player/CGS layer.

## 6. Information To Games

Sources:

- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/hacking/library/game-system/hacking/library/concurrent-game-system/docs/dev/journal/2026-05-24.md`
- `lab/hacking/library/being/doing/library/library/information/knowing-as-settling/knowing-as-settling.md`
- `lab/hacking/library/being/doing/library/library/information/aboutness/aboutness.md`

Current picture:

The repo identifies concurrent game systems as the typed theory of computing.
A concurrent game system is one running game: event structure, polarity, causality, conflict, symmetry, strategy, and admitted plays.
The same source asserts SPOTCOMP bridges: federation as parallel composition, embodied handedness as Player/Opponent duality, and name mobility as finite-support symmetry.
From the information side, knowing is settled substrate state and aboutness is predication participation.

SPOTCOMP consequence:

The games layer should be derived from informational asymmetry: players act from partial observations, strategies transform observed information into moves, and federation composes games by sharing trace evidence.
The modeled-player layer must keep game-theoretic Player/Opponent polarity distinct from SPOTCOMP modeled-player records.

Open obligation:

Define the functor from informational artifacts and receiver-relative settled states into CGS arenas, including observation maps, causality, conflict, polarity, symmetry, and strategy equivalence.

Current working surface: [INFORMATION-GAMES.md](./INFORMATION-GAMES.md), [schema/information-game-profile.schema.json](./schema/information-game-profile.schema.json), and [src/information-game-profile.mjs](./src/information-game-profile.mjs) check declaration-level preconditions for that functor.

## 7. Standards Boundary

Sources:

- `development/experimental/spotcomp/IETF-CONFORMANCE.md`
- `development/active/articulating/library/articulation-cell/library/potential-articulation-cell/predicating/library/predication-category/library/predication-cell-set/library/predicate-set/library/predicate-category/hacking/library/thing/library/system/library/operating-system/library/computer-operating-system/hacking/library/spotcomp/hacking/library/typed-resource-catalog/docs/dev/specification.md`

Current picture:

IETF/RFC obligations attach at stable byte, identifier, signature, HTTP, problem-details, and SHP/RFC-structured packet boundaries.
POSIX itself is not IETF, but when SPOTCOMP exports bytes over network protocols, canonical JSON, signatures, media types, HTTP semantics, and error objects must follow applicable RFCs.

SPOTCOMP consequence:

Do not bind an RFC to an object before the mathematical object boundary is fixed.
Once fixed, the byte/interface layer must be exact and testable.

Open obligation:

Publish media-type and transport profiles for traces, envelopes, regime records, SHP packets, and problem details, with test vectors for canonicalization and signature verification.
