# Player Character Boundary

Status: candidate declaration surface.
This file normalizes the agent, character, persona, role, skill, and modeled-player material before it is used as SPOTCOMP swarm conformance evidence.

## 1. Why This Boundary Exists

Archive and active sources use several near-neighbor terms.
They are useful, but they cannot be collapsed:

- an external player is the entity being modeled;
- a modeled player is the system-held local settling of that entity;
- a character is a computer-realized agentic record with persistent state, skills, governance, and identity surfaces;
- a persona is persistent identity over time;
- a role is a context-specific bundle of skills and authority;
- a skill is a typed decision/operator surface;
- a method or tool surface is the callable execution layer beneath skills;
- a CGS strategy is the game-facing behavior over observation and action events.

If these are collapsed, a public key, inbox, or tool list can be mistaken for a modeled player.
That is not enough for SPOTCOMP.

## 2. External Player And System Model

The old player schema is useful because it says the player itself is external and the system holds a settling that represents the model.
SPOTCOMP should preserve that distinction.

A modeled-player declaration must therefore name:

- the external player reference;
- the system-held model reference;
- the local settling that carries the model;
- the player kind, such as character, peer, operator, inference-model, application, user, system, or observer;
- the observation, action, capability, and governance bounds used to admit moves.

The model may be a model of a character, a peer, an operator, or another system.
A character is one possible player kind, not the definition of player.

## 3. Character, Persona, Role, Skill

The agent hierarchy sources give a practical stratification:

- persona: persistent identity over time;
- role: context-specific bundle of skills and authority;
- skill: typed decision procedure or admissible operator surface;
- method/tool surface: callable operation that a skill may invoke.

The active character sources add that a character is a system-resident record with identity, governance, skill generators, memory or journaling surfaces, and installation/projection surfaces.
Teaching a skill to a character is substrate-side predication on the bearer record; installing a character into a host is a downstream host-environment projection.

SPOTCOMP implementations must keep those steps distinct:

- teaching changes the character's substrate predication state;
- installation realizes that state in a host environment;
- player binding uses the character record to model strategy-bearing behavior;
- federation uses signed traces and governance, not character identity alone.

## 4. Agentic State

The agential semioverse and agent structure sources describe an internal agent as having bounded internal state, admissible interaction operators, policy, memory fragment, epistemic profile, normative profile, and local flow/nucleus structure.

For SPOTCOMP, this means a character-to-player binding should provide:

- bounded internal state or memory fragment;
- epistemic/update surface;
- normative/governance surface;
- skillset as admissible operators;
- monotone observation update behavior;
- local flow/nucleus or sigma/delta commutation evidence;
- failure monotonicity and provenance preservation for operations.

These are declaration obligations until proved.
The current checker records that the obligations are named and sourced.

## 5. CGS Boundary

A modeled player becomes game-facing only by binding to a CGS strategy profile:

- observation maps produce candidate Opponent events;
- player actions produce Player events;
- governance checks and local settlement supply causality;
- incompatible moves or rejected admissions supply candidate conflict;
- player, replica, name, and delivery-order equivalences supply symmetry candidates.

Polarity remains game-theoretic structure, not identity.
A character can be the actor of a Player event in one arena while information about that same character appears as Opponent input to another strategy.

## 6. Implementation Boundary

A conforming implementation surface should not accept a player record as complete when it has only an identifier, key, inbox, and outbox.
It must also declare:

- external-versus-model boundary;
- local settling reference;
- character/persona/role/skill references when the player kind is character;
- handedness and observation/action bounds;
- governance and capability checks;
- CGS strategy/profile reference;
- evidence that teaching, installation, and player binding are distinct steps.

The declaration probe [src/player-character-profile.mjs](./src/player-character-profile.mjs) checks this boundary.
It does not prove local-settling correctness, skill admissibility, modal governance, host installation correctness, CGS receptivity, or strategy composition.

Role recognition is handled by [RECOGNITION.md](./RECOGNITION.md).
A character or modeled-player record may name a role, but SPOTCOMP swarm conformance requires the role to be admitted through recognition cells and governance rather than by a flag alone.
