# Trace Axis Declaration Profile

Status: candidate declaration surface.
This profile is a guardrail around the trace object while D1 remains open; it is not a complete derivation of the trace object from positing.

## 1. Problem

The active trace sources do not identify a SPOTCOMP trace with a row list alone.
A predication-cell trace carries at least:

- discrete event records: positing entries, closure-firing entries, and originating articulating acts;
- temporal and causal precedence;
- bilattice-valued evidence trajectory;
- recognition fiber;
- categorical refinement structure between traces;
- constitutive-act provenance DAG.

EAVT JSONL is the finite computer carrier for transactionally located trace rows.
It is not an extra object around FOUR, and it is not the full trace object.
A conforming profile must therefore say which axes are present in the source trace, which axes a finite presentation preserves, and which axes a projection intentionally forgets.

## 2. Profile Object

`trace-axis-profile` declares:

- the trace object and its carrier presentation;
- the six required axes and the evidence for each axis;
- finite event records whose rows, when present, are exact `{e,a,v,t}` EAVT rows;
- causal precedence edges and constitutive provenance references;
- a trace-monoid independence relation for commuting steps;
- directed-join law declarations for trace growth;
- projections with explicit preserved and forgotten axes;
- a presentation boundary forbidding hidden row fields from standing in for the richer trace.

This keeps the finite row carrier useful without allowing it to define away causal, recognition, refinement, or provenance structure.

## 3. Required Axes

The required axis names are:

- `event-record`
- `temporal-causal-precedence`
- `evidence-trajectory`
- `recognition-fiber`
- `categorical-refinement`
- `constitutive-provenance`

Each axis needs source evidence and at least one preservation mechanism, checker, or projection that accounts for it.
A finite EAVT presentation may forget axes, but it must say so.

## 4. Event Records And Rows

Every event has one of these kinds:

- `originating-articulating-act`
- `positing-entry`
- `closure-firing-entry`

When an event carries a row, that row has exactly `e`, `a`, `v`, and `t`.
Axis data is not added as row fields.
Extra trace structure lives in the profile object or in derived trace resources with their own typed carrier.

## 5. Provenance And Causality

Constitutive provenance is accumulative.
If event `x` cites event `p` as provenance, then the profile must also contain a causal edge from `p` to `x`.
The validator checks reference existence, direct provenance edges, and acyclicity of the causal graph.
It does not prove the full source theorem; it prevents profiles from hiding non-accumulative provenance behind unordered rows.

## 6. Independence Relation

The independence relation is trace-monoid shaped: pairs are irreflexive, cite known steps, and cannot be causally ordered in either direction.
The declaration treats the listed pairs as a symmetric relation by requiring `symmetricClosureDeclared: true`.

This is still weaker than the missing functor from abstract history systems to settlement lattices.
It is enough to keep implementation probes from confusing row interleaving with mathematical independence.

## 7. Projection Boundary

A projection records:

- `kind`, such as `finite-row-presentation`, `trace-monoid-summary`, or `semantic-hypertext-packet`;
- `preservedAxes`;
- `forgottenAxes`;
- source frontier;
- output kind;
- evidence.

Preserved and forgotten axes must be disjoint.
Finite row presentations must forget at least recognition fiber, categorical refinement, and constitutive provenance unless those axes are carried by separately declared resources.

Recognition preservation is detailed in [RECOGNITION.md](./RECOGNITION.md).
In particular, parse success and finite shape recognition do not by themselves carry the `recognition-fiber` axis or admit a row into a receiver's local settlement.

## 8. Open Derivation

This profile does not close D1.
It supplies a declaration-level checker for the boundary between trace event, finite row carrier, and projection artifact.
A final SPOTCOMP implementation still needs the positing-to-trace derivation, naturality under reindexing, and the trace-monoid-to-settlement functor.
