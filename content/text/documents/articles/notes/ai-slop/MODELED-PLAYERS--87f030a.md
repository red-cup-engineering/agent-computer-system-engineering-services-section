# Modeled Players And Concurrent Games

Status: derivation sketch.
This file records the current modeled-player surface, but [DERIVATION-OBLIGATIONS.md](./DERIVATION-OBLIGATIONS.md) D9 blocks final modeled-player conformance.

## 1. Why This Layer Exists

SPOTCOMP swarms are not just replicated logs.
They are concurrent systems whose participants observe, decide, and act under bounds.
To make agents implementable and auditable, those participants must be modeled.

## 2. Local Settling Before Player Records

The repo's local-settling note makes modeled-player state a special case of object-local settling.
A modeled player's settling is SPOTCOMP's model of that player's predication state.
Therefore player records are downstream of local closure behavior, not just authentication metadata.

[CLOSURE-SETTLING.md](./CLOSURE-SETTLING.md) records the current declaration boundary for this claim: local settling is a bounded restriction of the universal sigma/delta closure cycle, and modeled-player state may occupy that position only when it carries the same restriction and fixed-point obligations.

An implementation must preserve:

- the player's partial observation frontier;
- the player's local closure rules and local fixed-point state;
- the embedding of that local settling into the universal settling;
- the governance and capability bounds that make proposed moves valid or invalid.

[AGENTIC-EMBEDDING.md](./AGENTIC-EMBEDDING.md) supplies the current candidate bridge from computer-realized characters and swarms to this modeled-player layer.
It keeps character governance, skills, and state distinct from modeled-player local settling and CGS strategy obligations.

[PLAYER-CHARACTER-BOUNDARY.md](./PLAYER-CHARACTER-BOUNDARY.md) adds the current normalization surface for player terminology: external player, modeled player, character, persona, role, skill, method/tool surface, and CGS strategy are distinct positions.
A character is one possible player kind, not the definition of player.

[BIGRADED-DIAMOND-SWARMS.md](./BIGRADED-DIAMOND-SWARMS.md) adds the current swarm-mathematics correction: a modeled player must also be readable as an observer-local settling in a multi-observer system `V : O -> Settlings_B`, with truth-axis and knowledge-axis obligations preserved.
Key identity, inbox/outbox shape, and CGS event declarations are not enough when the swarm claim depends on common knowledge, consensus, disagreement, or aperiodic tiling.

[MODELED-PLAYER-SWARM-DYNAMICS.md](./MODELED-PLAYER-SWARM-DYNAMICS.md) refines this into the current ruled-observer surface: a modeled player is an external player represented by an observer-local settling `V(o)` and per-observer rule system `r(o)`, with agentive positing, network-sheaf consensus, transition dynamics, and aperiodic witness obligations preserved before CGS strategy claims are reviewed.

[CONTINUOUS-LEARNING.md](./CONTINUOUS-LEARNING.md) adds the current learning boundary: a modeled player can change along its trajectory only through governed trace-bearing predication, teaching, skill-closure, memory-fragment, or rule-system transition evidence.
Hidden adaptation is not modeled-player learning evidence.

## 3. Modeled Player

A modeled player is a tuple:

`P = (id, K, Cap, Obs, Act, Gov, In, Out, Strat)`

where:

- `id` is a stable player identifier.
- `K` is an identity key or local authenticated authority.
- `Cap` is a finite capability declaration.
- `Obs` is an observation-bound function.
- `Act` is an action-bound function.
- `Gov` is the governance regime constraining valid actions.
  The current candidate profile is [GOVERNANCE.md](./GOVERNANCE.md), which treats authorization as modal restriction over exact EAVT governance rows.
- `In` is an EAVT inbox trace.
- `Out` is an EAVT outbox trace.
- `Strat` is the player's strategy over observed histories.

`In` and `Out` are not messages with special semantics.
They are EAVT traces.

The tuple is still incomplete for strong conformance unless it is tied to an external player/model boundary and local settling.
The active player schema says the player itself is external while SPOTCOMP holds a settling representing the model.
Implementations therefore need both an external-player reference and a modeled-player reference, with the local settling named as the model carrier.

## 4. Handedness

For implementation, a modeled player has handedness:

`h(P) = (recv, send, actuate, observe)`

Each component is a bound:

- `recv`: what the player can receive or parse.
- `send`: what the player can emit.
- `actuate`: what tools or world actions the player can perform.
- `observe`: what trace/world portions the player can inspect.

These bounds are first-class because agents in a swarm are structurally asymmetric.

## 5. Concurrent Game Reading

A SPOTCOMP swarm can be read as a concurrent game with symmetry:

- Events are trace appends, observations, settlements, and federated deliveries.
- Polarity distinguishes environment/opponent moves from player moves.
- Causality orders events that depend on prior observations or settlements.
- Conflict records incompatible moves or governance-invalid choices.
- Symmetry identifies events equivalent up to player renaming, replica renaming, or independent delivery order.
- Strategies are modeled-player policies that produce valid outbox traces from observable histories.

The target category is CGS: objects are prime event structures with causality, conflict, polarity, and symmetry; morphisms are concurrent strategies on `A^perp || B`, modulo the relevant symmetry equivalence.
Sequential or innocent strategies are special cases, not the general swarm model.

This profile does not claim the full categorical embedding is complete.
It uses the concurrent-game reading to set implementation obligations and records the proof gap in [GAPS.md](./GAPS.md), [CATEGORICAL-MACHINERY.md](./CATEGORICAL-MACHINERY.md), [CGS-EMBEDDING.md](./CGS-EMBEDDING.md), and [DERIVATION-OBLIGATIONS.md](./DERIVATION-OBLIGATIONS.md) D9.

The current declaration surface is [CGS-EMBEDDING.md](./CGS-EMBEDDING.md).
It requires explicit candidate events, Player/Opponent polarity, causality, minimal conflict pairs, symmetry classes, and strategy bounds before a modeled-player record can be reviewed as CGS-shaped.

[CGS-STRATEGY-LAWS.md](./CGS-STRATEGY-LAWS.md) records the next strategy-law layer: a CGS morphism is a concurrent strategy on `A^perp || B`, modulo symmetry, with receptivity and interaction-and-hiding composition obligations.
A modeled player loop or key identity is not a strategy equivalence proof.

[PLAYER-CHARACTER-BOUNDARY.md](./PLAYER-CHARACTER-BOUNDARY.md) binds this to the agentic side: observations produce candidate Opponent events, player actions produce Player events, and polarity remains game structure rather than identity.

## 6. Swarm

A swarm is a finite or directed family of modeled players sharing a federation discipline:

`S = (Players, SharedTrace, Fed, Gov, Settle)`

where:

- `Players` is the current modeled-player set.
- `SharedTrace` is the merge of admitted player traces.
- `Fed` is the authenticated delivery and merge relation.
- `Gov` validates capabilities and action bounds.
- `Settle` projects the shared trace into finite artifacts.

A swarm implementation MUST support player-local partial observation.
It MUST NOT assume that every player sees the same trace frontier at the same time.

For strong swarm claims, the family of modeled players must additionally declare the bigraded-diamond surface:

- the closure KZ and fibration KZ axes remain separated;
- consensus is a limit or `H0` construction over observer-local settlings;
- disagreement preserves `H1_t` and `H1_top` audit positions when relevant;
- per-observer rule systems name their closure ordinals or regime evidence;
- aperiodic tiling claims cite a substitution, patch, direct-limit, or regime witness.

If the swarm is used in a UAS context, DRIP/Remote ID identity and authentication obligations remain separate from this tiling structure.

## 7. Normative Player Records

A player record SHOULD be EAVT-expressible.
At minimum it needs rows equivalent to:

```json
{"e":"player:alice","a":"has-public-key","v":"did:key:z...","t":"2026-05-27T00:00:00Z"}
{"e":"player:alice","a":"has-capability","v":"settle-shp","t":"2026-05-27T00:00:00Z"}
{"e":"player:alice","a":"observes","v":"trace:inbox/alice","t":"2026-05-27T00:00:00Z"}
{"e":"player:alice","a":"emits","v":"trace:outbox/alice","t":"2026-05-27T00:00:00Z"}
```

The exact `e` and `v` identifier schemes are implementation-defined, subject to URI and JSON conformance requirements in [IETF-CONFORMANCE.md](./IETF-CONFORMANCE.md).
