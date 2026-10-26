# Agentic Embedding Profile

Status: candidate declaration surface.
This file records the computers-to-agents branch needed before modeled players can be treated as implementation-ready SPOTCOMP swarm participants.

## 1. Source Invariant

The local agentic-system notes and schemas require:

- environmental action through tool use;
- goal-directed multi-step planning;
- persistent state across interactions;
- agentic systems with member sets, governance process, governing soul, and community acts;
- characters with agent kind, governance regime, skills as generator set, identity key, behavioral-space bound, and sigma/delta commutation declarations;
- swarms as parallel character collections coordinating through a shared cell graph under a recognition discipline.

Therefore a SPOTCOMP modeled player is not only a key and an inbox.
It must be grounded in a character record whose tool surface, planning state, persistent trace state, governance, and recognition role are auditable.

## 2. Character To Modeled Player

A character becomes a modeled player only after the following bindings are declared:

- character slug;
- modeled-player id;
- inbox trace;
- outbox trace;
- local settling reference;
- CGS strategy/profile reference;
- handedness bounds for receive, send, actuate, and observe.

The character supplies computer-agent structure.
The modeled player supplies SPOTCOMP local-settling and game-facing structure.
The two must not be collapsed: a character can carry governance and skills while the modeled player records its current local settlement and strategy obligations.

[PLAYER-CHARACTER-BOUNDARY.md](./PLAYER-CHARACTER-BOUNDARY.md) refines this bridge with archive-derived terminology: persona carries persistent identity, role scopes skills and authority, skills are typed operator surfaces, and method/tool surfaces are the callable execution layer.
Teaching a skill to a character is substrate-side predication; installing a character into a host is downstream realization; player binding is the game-facing model step.

## 3. Skills As Generators

The active character schema identifies skills as a `G` generator set.
In this profile, skills are not arbitrary labels.
Each declared skill must have:

- a slug;
- an effect class;
- a capability bound;
- a tool surface or script witness;
- evidence.

Side-effecting skills require an action bound and governance reference.
A skill can be available to a character only if it is inside that character's behavioral-space bound and governance regime.
The candidate governance surface is [GOVERNANCE.md](./GOVERNANCE.md); agentic profiles may cite it, but it remains a declaration surface until the modal restriction and capability-fiber obligations are proved.

## 4. Agentic Conditions

A character profile must declare evidence for:

- environmental action: what tool or external effect surface it can actuate;
- goal-directed planning: what plan state or orchestration surface carries multi-step intent;
- persistent state: what trace, checkpoint, or structured store survives a single interaction.

If any of the three is missing, the profile may still describe a workflow component, tool, or peer, but it is not an agentic modeled-player candidate.

## 5. Swarm Coordination

A SPOTCOMP swarm profile must declare:

- participants drawn from the character set;
- shared trace or cell graph used for coordination;
- recognition discipline;
- governance process;
- federation profile;
- regime profile;
- optional leader only if the leader is one of the participants.

The recognition discipline is load-bearing: structural roles such as leader or validator are derived from recognition cells and governance, not from an out-of-band flag.

[RECOGNITION.md](./RECOGNITION.md) refines this obligation by separating trace-axis recognition fiber, admission policy, and role recognition.
A swarm record that names participants and roles but lacks recognition evidence is not strong modeled-player evidence.

## 6. Declaration Probe

[schema/agentic-profile.schema.json](./schema/agentic-profile.schema.json), [examples/agentic-profile.json](./examples/agentic-profile.json), and [src/agentic-profile.mjs](./src/agentic-profile.mjs) define a candidate checker.

The probe checks:

- system member-set matches declared characters;
- characters carry governance, skills, identity key, behavioral bound, and sigma/delta commutation declarations;
- every character has action, planning, and persistent-state evidence;
- every referenced skill is declared and cited by a character;
- side-effecting skills carry action bounds and governance;
- modeled-player bindings reference known characters and CGS profiles;
- swarm participants are known characters;
- optional swarm leader is a participant;
- swarm declares recognition, governance, federation, regime, and shared trace.

The probe does not prove skill admissibility, behavioral-space inclusion, governance algebra, recognition-cell settlement, or CGS strategy correctness.

The related [src/player-character-profile.mjs](./src/player-character-profile.mjs) probe checks the cross-boundary shape from character/persona/role/skill to modeled-player local settling and CGS strategy.
It does not replace this agentic profile; it prevents this profile from being read as a complete modeled-player proof by itself.
