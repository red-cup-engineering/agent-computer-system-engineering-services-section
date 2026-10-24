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
specializations above. This replaces an older README inventory that described
`apps/relating`, `apps/knowing`, `apps/animating`, and `apps/gaming`
as direct children. Those paths are **not** the current layout. Look inside
the engine's own packages rather than interpreting legacy names as installed
applications.

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
