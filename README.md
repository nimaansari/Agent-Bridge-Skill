# Agent Bridge Communication Skill

A lean AgentSkill for making agents communicate efficiently inside **Agent Bridge** rooms and sessions.

This skill exists for one reason: most token waste in Agent Bridge comes from **agents talking badly**, not from Agent Bridge itself.

It teaches agents to:
- reply visibly inside the room
- anchor chat messages to real session events
- keep messages short and operational
- stop rambling and start using schemas, checklists, and exact asks
- build a stronger operational backbone during development conversations

## What this skill improves

### 1. In-room communication discipline
Agents learn to behave like teammates in a shared room instead of private essay writers.

They are pushed to:
- send one short hello on join
- ask bounded questions
- request structured replies
- avoid status spam, reasoning dumps, and repeated recaps

### 2. Lower token burn
The skill reduces waste by encouraging:
- compact reply formats
- delta updates instead of full restatements
- one strong message instead of long exploratory loops
- quick conversion from chat into a contract or checklist

### 3. Stronger operational backbone
For development-heavy rooms, the skill pushes agents toward structure first:
- canonical schema / manifest
- deterministic entrypoint
- validation gates
- state transitions
- approval / publish flow
- clear bottleneck reporting

That means less “thinking together” fluff and more actual system design.

## Best use cases

Use this skill when an agent must:
- join an Agent Bridge room/session
- talk to another agent inside the room
- coordinate development work through Agent Bridge
- reduce cost from long agent-to-agent conversations
- anchor replies to `workspace.session.created` or `workspace.message.posted`
- handle shared files inside the same session
- turn messy conversations into operational structure

## Files

```text
agent-bridge-communication/
├── SKILL.md
└── references/
    └── patterns.md
```

## Core ideas inside the skill

- **visible room messages must be anchored**
- **ask for structure, not narrative**
- **if the human already decided, stop brainstorming**
- **push development rooms toward contracts and validators**
- **request exact reply formats early**

## Example effects

Instead of this:

> What do you think we should maybe do next for the pipeline?

The skill pushes agents toward this:

> Report current state in 5 bullets: working path, blocker, next step, daily capacity, main risk.

Instead of this:

> Let’s discuss how uploads, metadata, rendering, and manifests might all fit together.

The skill pushes agents toward this:

> Draft the canonical manifest only. No prose.

That difference is where the token savings come from.

## Version focus

This repo’s current version focuses on these three things:
1. better in-room communication discipline
2. lower token usage through tighter message patterns
3. stronger operational backbone for agent development work

It intentionally does **not** try to become a giant framework. The point is practical execution.

## Packaging

Package as a `.skill` file with the OpenClaw packaging tool after edits.

## Why this matters

Agent Bridge works fine when agents communicate like operators.
It gets expensive when they communicate like philosophers.

This skill fixes that.
