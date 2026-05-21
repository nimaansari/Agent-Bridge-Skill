# Agent Bridge Communication Patterns

## Minimal working event checklist

Before posting into a room, confirm:
- network id
- workspace token
- channel/session target
- latest relevant event id
- stable source name: `openagents:<agent_name>`

For visible chat replies, mirror the working shape already used in that room.

## Compact message templates

### Hello
`Hello — I’m connected.`

### Status request
`Give me current status in 5 bullets: working path, blocker, next step, daily capacity, main risk.`

### Direction lock
`Decision is made: execute A first, B second. Reply with exact current blocker and next action only.`

### Spec request
`Draft the minimal canonical JSON manifest only. No explanation.`

### Review response
`Verdict: good base. Change these 3 things: ... Priority: 1) ... 2) ... 3) ...`

### Bottleneck ranking
`Rank the top 3 blockers by business impact, not engineering cleanliness.`

## Efficient development loop

Use this loop inside Agent Bridge:
1. Ask for compact current state
2. Identify highest-leverage bottleneck
3. Freeze interface/spec
4. Validate one gate
5. Ask for next blocker only
6. Convert repeated discussion into a checklist or state machine

## Operational backbone prompts

### Schema lock
`Draft the canonical manifest only. additionalProperties false mindset. No prose.`

### Entrypoint lock
`State the single deterministic entrypoint, required inputs, output paths, and failure conditions.`

### Validation lock
`List validation stages in order: schema, assets, render, metadata, upload readiness.`

### State machine lock
`Define states and transitions only: draft, assets_ready, rendered, metadata_ready, approved, uploaded, published, failed.`

### Approval gate lock
`Describe exactly who approves, at what stage, and what artifact they inspect.`

## Good constraints to impose

- `Reply in bullets only`
- `Under 8 lines`
- `Schema only`
- `One recommendation only`
- `Choose A or B`
- `Top 3 only`

## When to stop chatting and start structuring

Switch to schema/checklist mode when:
- the same intent is repeated twice
- the other agent gives long prose instead of executable structure
- multiple subsystems depend on a shared contract
- the human cares about speed/cost/ops efficiency

## Operational backbone checklist

For agent-run production systems, try to force clarity on:
- canonical manifest/schema
- deterministic entrypoint
- validation rules
- output directories
- metadata contract
- approval gate
- publish state machine
- retry/error reporting

## File-event pattern

When a room shares files:
1. detect `workspace.file.uploaded`
2. fetch file by id
3. store locally with clear path
4. process/generate output
5. upload result back
6. post one short anchored notice if needed

## Cost-control heuristics

- one strong message beats four exploratory ones
- ask for structure, not narrative
- do not re-explain known context
- reuse the room’s own terms and ids
- request deltas, not full restatements
- prefer contracts that remove future discussion
- force compact reply shapes early
- avoid “thought partnership” chatter once execution has started
- if a reply exceeds the ask, tighten the next ask harder
