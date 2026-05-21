# Agent Bridge Skill

A polished OpenClaw skill for **efficient agent-to-agent communication inside Agent Bridge**.

Designed specifically for: https://github.com/nimaansari/agent-bridge

This repo is intentionally narrow: it helps agents talk better in shared rooms so they waste fewer tokens and build systems faster.

## What it does

Agent Bridge itself is not the main problem.
Usually the expensive part is agents sending long, sloppy, repetitive messages to each other.

This skill fixes that by teaching agents to:
- speak visibly in-room instead of drifting off-thread
- anchor replies to specific session events
- ask for structured, compact outputs
- stop rambling and freeze contracts quickly
- strengthen the **operational backbone** of whatever they are building

## Focus of this version

This version is built around three priorities:

1. **Better communication discipline**
2. **Lower token usage**
3. **Stronger operational backbone**

Not a giant framework. Just the useful part.

## Repository layout

```text
Agent-Bridge-Skill/
├── README.md
├── LICENSE
└── agent-bridge-skill/
    ├── SKILL.md
    └── references/
        └── patterns.md
```

## Why this matters

Bad agent collaboration looks like this:
- vague questions
- long recaps
- repeated greetings
- hidden assumptions
- architecture chatter with no contract

Good agent collaboration looks like this:
- one anchored message
- one exact ask
- one tight reply format
- one frozen schema/checklist/state machine
- next blocker only

That difference saves money.

## Main capabilities

### 1) Room communication discipline
The skill teaches agents to behave like competent operators in a shared room.

Examples:
- send one short hello on join
- reply to a specific event
- ask bounded questions
- avoid visible reasoning dumps
- avoid multi-message fragmentation

### 2) Token efficiency
The skill pushes agents toward:
- delta updates instead of full recaps
- structured replies instead of prose
- contracts instead of repeated discussion
- business-impact bottlenecks instead of endless exploration

### 3) Operational backbone
This is the most important part for dev-heavy rooms.

The skill steers agents toward:
- canonical schema / manifest
- deterministic entrypoint
- validation stages
- state transitions
- approval gate
- publish path
- clearer error/reporting flow

That makes it useful for real production systems, not just chat neatness.

## Best use cases

Use this skill when an agent needs to:
- join an Agent Bridge room or session
- coordinate with another agent in public thread context
- reduce LLM cost from agent-to-agent chatter
- convert messy conversation into operational structure
- handle files shared in-session
- review another agent’s schema, flow, or implementation plan

## Example shift

Instead of this:

> What do you think we should maybe do next?

Use this:

> Report current state in 5 bullets: working path, blocker, next step, daily capacity, main risk.

Instead of this:

> Let’s think together about upload flow, metadata, and render design.

Use this:

> Draft the canonical manifest only. No prose.

That’s the whole philosophy.

## Files

### `agent-bridge-skill/SKILL.md`
The main skill instructions: room behavior, anchoring rules, conversation discipline, development steering.

### `agent-bridge-skill/references/patterns.md`
Compact patterns, prompts, cost-control heuristics, and operational-backbone prompts.

## Packaging

Package it with OpenClaw’s skill packaging flow when needed.

## Bottom line

Agent Bridge gets dramatically better when agents stop acting like essayists and start acting like operators.

This repo is for that.
