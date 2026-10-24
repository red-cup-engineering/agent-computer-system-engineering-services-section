# A first experience with two real agentic engine faculties

The [example arena](agent-family-arena.json) is a genuine input to the
maintained `@red-cup-engineering/agentic-orchestration-platform@0.2.0`
dispatcher, not pseudocode. It contains **two local player labels**
(`reader` and `designer`) and three source-backed moves:

1. `normalize-input` calls `relation canonicalize` on JSON.
2. `design` calls `play design` on an admitted play entry.
3. `normalize-output` calls `relation canonicalize` after **both**
   earlier moves succeed. The existing arena enforces the causal relation.

All three actions run through the original induced action registry and
the actual finite concurrent-game dispatcher. Each resulting receipt has
an exact move identifier, origin player label, status, exit code, standard
output, and standard error. A missing dependency, declined action or
unknown acknowledgment is **not** reported as successful work.

## Run it

After checking out the parent public section, use an isolated installation
of the separately maintained package (so the parent section's own
`workspace:*` dependencies do not become an installation requirement):

```sh
example_dir="$(mktemp -d)"
npm install --prefix "$example_dir" \
  @red-cup-engineering/agentic-orchestration-platform@0.2.0 \
  --registry=https://registry.561.group/
"$example_dir/node_modules/.bin/multi-agent-engine" arena play \
  < examples/agent-family-arena.json
```

A reproducible source-owned consumer receiving run is declared at
[the GitHub Actions workflow](../.github/workflows/agent-first-experience.yml).
It installs the existing package separately and exercises the exact example;
a green result confirms only this published-package scenario and its output,
not a live hosted service. Check the workflow's execution result before
claiming that receiving succeeded.

## Independently observed first run

[GitHub Actions run 40134596039](https://github.com/red-cup-engineering/agent-computer-system-engineering-services-section/actions/runs/40134596039)
installed the existing version `0.2.0` package into an isolated consumer
directory, then ran **this exact JSON file** with no substituted engine.
The three receipts were:

```text
normalize-input   succeeded   {"a":1,"z":9}
design            succeeded   {"entries":[{"locus":[],"reading":"stable"}]}
normalize-output  succeeded   {"b":2,"c":3}
```

The dependency installation was substantial: the runner reported **810
packages in approximately four minutes**. That is a real onboarding and
distribution cost, not a claim that this experience is lightweight. The
result establishes this particular packaged consumer route; it does not
prove the private source checkout is publicly accessible or that a deployed
agent system exists.

## What this does and does not demonstrate

This experience exercises genuine components and their cross-engine
composition. It does **not** start a ChatGPT, Claude, or Codex process,
authorize a remote agent, persist a task board, register an Actor office,
or deploy MetroPlat. The player identifiers are descriptive values within
one bounded arena, not institutional identities or credentials.

If you want a decision tool rather than execution orchestration, the
[attention-allocation readout](https://github.com/red-cup-engineering/attention-allocation-readout-service)
offers a different source-backed starting point: give the actual
Metrologic operator a finite budget and explicit costs and benefits using
`attention-plan`. Its selection is not itself evidence of Work completion.

For **source ownership**, follow the parent engineering README to the
harness, individual-agent, multi-agent, and hosting sections. Some GitHub
submodule implementations are private; this public example does not
relicense or expose their code.
