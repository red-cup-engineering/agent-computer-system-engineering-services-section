# Bigraded Cohomology Audit Profile

Status: candidate declaration surface.
This file records the audit vocabulary SPOTCOMP needs for regime-aware federation and paraconsistent swarm audit without requiring every implementation to compute full sheaf cohomology.

## 1. Source Invariant

The local cohomology sources split a paraconsistent settling-associated sheaf into:

- truth-designated component `F_U^(t)`;
- inconsistency component `F_U^(top)`.

The bigraded cochain complex has two non-zero designation rows:

- `m = 0`: truth-designated content;
- `m = 1`: knowledge-top/inconsistency content.

The cohomological degree axis is the ordinary cochain degree `n >= 0`.
SPOTCOMP's first audit surface focuses on degree `n = 1`:

- `H1_t = H^{0,1}`: first-order obstruction on the truth side;
- `H1_top = H^{1,1}`: first-order obstruction in inconsistency content.

This is not scalar validity.
A swarm that records only "valid" or "invalid" erases the distinction between truth-side obstruction and inconsistency-side obstruction.

## 2. Regime Consequence

The four closure-ordinal regimes determine how much cohomological evidence federation must preserve:

- strict and Scott-continuous regimes may claim first-cohomology vanishing with suitable regime evidence;
- transfinite-bounded and aperiodic regimes may carry non-trivial `H1_t` and `H1_top` content;
- endpoint-state alone is not enough evidence for transfinite-bounded or aperiodic claims;
- receivers that cannot verify a cohomology claim must downgrade the payload rather than treating it as final settlement.

This profile is the audit companion to [REGIME-FEDERATION.md](./REGIME-FEDERATION.md).

## 3. Inconsistency Sheaf Record

The inconsistency audit object tracks top-valued cells as substrate content.
A conforming declaration identifies:

- scope;
- top-cell references;
- witness citations;
- source classifications;
- stage ordinals;
- optional repair resolution references;
- cache/version identity when cohomology values are cached.

The source classifications used here are:

- federation-conflict;
- attack-surface;
- repair-source;
- local-inference;
- cross-source.

Top-cell membership is determined by the active value algebra and settlement, not by the classification label.

## 4. Slots And Claims

Each audit slot declares:

- slot name;
- designation grade `m`;
- cohomological degree `n`;
- component;
- claim;
- verification status;
- evidence.

The first required slots are:

- `H1_t`: `m = 0`, `n = 1`, component `truth`;
- `H1_top`: `m = 1`, `n = 1`, component `inconsistency`.

Claims may be `vanishes`, `nonzero`, `not-computed`, or `unknown`.
A not-computed or unknown claim is acceptable only when the receiver policy explicitly downgrades unverifiable payloads.

## 5. FOUR And K4 Projection

FOUR is not SPOTCOMP's substrate.
When a profile declares `fiberSpecialization = "FOUR"`, it must also declare the optional K4-sector projection as a projection-only audit surface.

The K4 sectors are:

- identity;
- negation;
- conflation;
- negation-conflation.

This records how the FOUR-specialized audit view projects automorphism sectors.
It does not make FOUR mandatory for other fibers.

## 6. Declaration Probe

[schema/cohomology-audit-profile.schema.json](./schema/cohomology-audit-profile.schema.json), [examples/cohomology-audit-profile.json](./examples/cohomology-audit-profile.json), and [src/cohomology-audit-profile.mjs](./src/cohomology-audit-profile.mjs) define a candidate checker.

The probe checks:

- designation grades include truth and inconsistency rows;
- cohomological degree declarations include degree `1`;
- `H1_t` and `H1_top` slots have the required coordinates;
- strict and Scott-continuous regimes do not declare nonzero `H1_top`;
- transfinite-bounded and aperiodic endpoint summaries require trajectory or cohomology audit evidence elsewhere;
- top-cell records cite witnesses and source classifications;
- unresolved or uncomputed cohomology claims require downgrade behavior;
- FOUR-specialized profiles include projection-only K4 sector declarations.

The probe does not compute cohomology, prove vanishing, decide top-cell membership from raw trace rows, or prove that a cached cohomology value is correct.
