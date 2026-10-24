# Agent Computer System Engineering Services Section

<!-- 561-group-standards:badges:start -->
[![Red Cup Engineering](https://img.shields.io/badge/561%20Group-Red%20Cup%20Engineering-c0392b)](https://github.com/red-cup-engineering)
[![License: MIT](https://img.shields.io/badge/license-MIT-c0392b)](LICENSE)
[![Indigenous data: CARE](https://img.shields.io/badge/Indigenous%20data-CARE-4b6f44)](https://github.com/red-cup-engineering/.github/blob/main/GOVERNANCE.md)
[![Tips welcome](https://img.shields.io/badge/tips-welcome-d4a017)](https://github.com/561-group/.github/blob/main/TIPS.md)
<!-- 561-group-standards:badges:end -->

**An engineering home for agent computer systems.** This repository connects
separately maintained engineering components that equip an agent to compute,
relate information, use tools, and work through bounded runtime interfaces.
It is a **source composition and engineering register**, not a single agent
you can install, a hosted assistant, or a command-line application.

## See an actual agentic system perform work

The public [three-move arena example](examples/agent-family-arena.json)
is a runnable input for the **existing** `multi-agent-engine` action
dispatcher. It uses two locally labeled players, two different engines,
and a causal dependency. A real first run returns the original action
receipts rather than merely displaying a README or mocking an agent.

With Node.js 22.18+ and the 561 Group package registry configured:

```sh
npm install @red-cup-engineering/agentic-orchestration-platform@0.2.0 --registry=https://registry.561.group/
./node_modules/.bin/multi-agent-engine arena play < examples/agent-family-arena.json
```

The `relation` engine canonicalizes JSON, the `play` engine runs its
existing design action, and a third move waits on both. This demonstrates
source-owned action **composition**, not hosted agents, authenticated Actor
offices, durable autonomous behavior, or public MetroPlat access.
See the [first-experience walkthrough](examples/README.md) for the actual
interfaces and what their receipts mean.

The separately maintained
[attention-allocation readout](https://github.com/red-cup-engineering/attention-allocation-readout-service)
offers a second concrete starting point: `attention-plan --run-example`
uses the original finite-budget mathematical selection to choose among
explicitly scored obstructions. It **does not execute those obstructions**.

This parent is a **public source map**. Its
[Agent Organization Engine](https://github.com/red-cup-engineering/agent-organization-engine)
source is currently private and requires separate authorized access.
The package installation above depends on its registry availability;
the public map alone is not a copy of private implementation source.

## Where to begin

The directories below are the current checked-in entry points. A Git
submodule points to a separate repository; follow its own README and package
manifest for implementation and usage.

| Entry | What you will find |
| --- | --- |
| [Agent Organization Engine](apps/agent-organization-engine) | The composed engine providing nine related agent faculty packages; package-level entry points live in its own `lib/` packages, **not** as separate apps at this repository root |
| [Agent harness systems](services/agent-harness-computer-system-engineering-services-section) | The boundary that equips and constrains one agent computer system |
| [Multi-agent computer systems](services/multi-agent-computer-system-engineering-services-section) | Engineering for systems constituted across multiple agents, separate from platform hosting |
| [Agent computer platforms](services/agent-computer-platform-system-engineering-services-section) | The durable hosting and operating boundaries for agent computer systems |
| [Task-management systems](services/task-management-computer-system-engineering-services-section) | The local engineering area for resolving identifiers and organizing task operations |

Read [the Agent Organization Engine source](https://github.com/red-cup-engineering/agent-organization-engine)
for faculty exports, tests, and its current architectural boundaries. Its
root package is a grouping manifest, **not** a root-level CLI. Its faculties
are `relating`, `communicating`, `knowing`, `playing`, `animating`,
`computing`, `socializing`, `gaming`, and `organizing`.

## What exists here

At the current repository root, `apps/` holds the
`agent-organization-engine` submodule, while `services/` holds the
specializations above. An older README treated faculty names as if they were separate applications
at this root. That inventory is obsolete. Follow the actual engine submodule
and its package manifests rather than guessing an installed application path.

The repository also carries a code-oriented register of earlier work on the
agent-computing corpus (previously called relational computing). Its paired
theory/research register is science-side, under the agent-related material in
[the Computer Science Services Section](https://github.com/lenticule-science/computer-science-services-section).
Source presence alone is not evidence of a running deployment or of complete
standards conformance.

## Scope and limitations

A **single agent system**, a **multi-agent system**, and a **platform hosting
agent systems** are different engineering responsibilities. Their repositories
own their respective executable components, compatibility claims, tests, and
release status. This section indexes and composes them; it does not inherit
their deployment guarantees, privileges, or runtime authority.

Changes to the family should start with the owning component's current
Issues, pull requests, branches, README, and package exports before changing
this index. That prevents a public-facing summary from getting ahead of the
software it describes.
