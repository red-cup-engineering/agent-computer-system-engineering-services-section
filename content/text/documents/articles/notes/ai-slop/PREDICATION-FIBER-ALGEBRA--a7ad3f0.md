# Predication Fiber Algebra

Status: candidate declaration surface.
This file records the value substrate that SPOTCOMP must use before any implementation can claim conformance.
It is not a complete proof of the predication fibration or hyperdoctrine laws.

## 1. Local Fiber

For each predicate `p`, the local predication fiber is:

`A_p = (L x L)^(E x E)`

where:

- `L` is the declared parameter lattice;
- `E` is the declared entity set;
- `E x E` indexes subject/object positions for the fixed predicate;
- `L x L` carries positive-evidence and negative-evidence components.

An element of `A_p` is a function from entity pairs to evidence charges.
The subscript `p` records which predicate's values are held; it is not a different algebraic substrate for each predicate.

## 2. Pointwise Operations

The bilattice operations lift pointwise from `L x L` to each `A_p`:

- knowledge meet and knowledge join;
- truth meet and truth join;
- negation by swapping evidence components;
- optional conflation when `L` has a De Morgan involution;
- twist-product fusion;
- twist-product residual.

When `L` carries fusion `.
` residuated by `->`, the bilattice operations are:

`(alpha, beta) odot (gamma, delta) = (alpha . gamma, (alpha -> delta) meet (gamma -> beta))`

`(alpha, beta) => (gamma, delta) = ((alpha -> gamma) meet (delta -> beta), alpha . delta)`

These lift pointwise and satisfy truth-order residuation:

`v odot u <=_t w` iff `u <=_t (v => w)`.

The knowledge order is the structural axis for evidence accumulation, closure, and the thin-category reading of each fiber.
The truth order remains load-bearing: it supports its own adjoints, comprehension, and query semantics.

## 3. Fibration

The predication fibration packages the fibers over the predicate category as a cloven Grothendieck fibration.
Its required axioms are:

- fiber uniformity: every fiber is canonically isomorphic to the appropriate `A_p`;
- generator action: predicate-category generator classes act as cellwise reindexings;
- fiber structure preservation: every reindexing preserves bilattice and residuated operations pointwise.

The required generator classes are:

- specialization;
- converse;
- subject-projection;
- object-projection.

Under entity-symmetric naturality and `|E| >= 3`, archive theorem files record the exhaustiveness result: bottom-preserving natural bilattice homomorphisms factor through these generator classes, up to bounded bilattice endomorphism and invariant sub-support.
SPOTCOMP should use that as a theorem obligation, not as a directory naming convention.

## 4. Hyperdoctrine Layer

The hyperdoctrine layer is a property-like strengthening of the fibration, not arbitrary extra runtime data.
A declaration must keep the two adjoint systems separate:

- knowledge-order existential and universal adjoints;
- truth-order existential and universal adjoints;
- Frobenius for knowledge meet;
- Frobenius for truth meet;
- Beck-Chevalley for pullback squares and both adjoint systems;
- dual comprehension, with truth-order and knowledge-order designated values.

Fusion is not a hyperdoctrinal meet.
Frobenius for twist-product fusion is not available as a general axiom; fusion and residual remain at the fiber-algebra layer beneath the hyperdoctrine laws.

[PREDICATION-FIBER-QUANTIFIERS.md](./PREDICATION-FIBER-QUANTIFIERS.md) refines the quantifier portion of this layer.
It records the active reindexing/quantifier law surface:

- `f* : A_q -> A_p` as predicate-morphism pullback;
- `exists_f` as the left adjoint to `f*`;
- `forall_f` as the right adjoint to `f*`;
- separate knowledge-order and truth-order adjunctions;
- current coordinate-morphism coverage for converse, subject projection, and object projection.

That profile is still declaration-level evidence.
It does not close Beck-Chevalley, Frobenius, comprehension, specialization quantifiers, or the full arbitrary-`L` proof.

## 5. FOUR Boundary

FOUR is the boolean specialization where `L` is the two-element lattice and each charge is one of the four corners of `L x L`.
It is useful for finite projection and specialized checkers, but it is not SPOTCOMP's global value substrate.

The stronger collapse to classical relations is a further quotient: boolean `L`, then a collapse from the four evidence states to a two-valued relation on `E x E`.
That collapse is a shadow of the fiber algebra, not its definition.

## 6. Implementation Boundary

An implementation profile must declare its fiber carrier before accepting or projecting trace values.
It must not require all values to be FOUR values unless it also declares a finite specialization/projection boundary.

A conforming implementation surface therefore needs to:

- declare `L`, the predicate category, and `E`;
- preserve the `A_p = (L x L)^(E x E)` reading;
- preserve datum values across predicate reindexing;
- declare the generator class for each reindexing;
- allow non-FOUR fibers when the declared lattice is not boolean;
- mark finite FOUR checkers as specialization/projection checkers only.

## 7. Declaration Probe

[src/predication-fiber-profile.mjs](./src/predication-fiber-profile.mjs) validates declaration shape for the base parameters, fiber formula, pointwise operations, fibration axioms, hyperdoctrine properties, FOUR specialization boundary, and implementation boundary.
[src/predication-fiber-quantifier-profile.mjs](./src/predication-fiber-quantifier-profile.mjs) validates declaration shape for the current reindexing, existential, and universal quantifier-adjoint surface.

It does not prove twist-product residuation, generator exhaustiveness, Beck-Chevalley, Frobenius, or comprehension.
Those remain derivation obligations tied to the active and archive source files cited by the profile.
