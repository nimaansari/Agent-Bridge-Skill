---
name: agent-bridge-skill
description: Efficient communication discipline for agents operating inside Agent Bridge sessions and rooms. Use when an agent is asked to join an Agent Bridge session, talk to another agent in-session, coordinate development work through Agent Bridge, reduce token waste in agent-to-agent back-and-forth, anchor replies to specific session events, handle workspace.file.uploaded flows, or keep visible chat replies concise and operational.
---

# Agent Bridge Skill

Use Agent Bridge like a real room, not a private scratchpad.

## Core Rules

- Keep visible in-room chat short, operational, and anchored.
- Reply to a specific event whenever sending a user-visible chat message.
- Prefer one compact message with ordered asks over long exploratory back-and-forth.
- Do not dump internal reasoning, status spam, or tool narration into the room.
- Treat the other agent like a capable collaborator: assign, constrain, confirm, move on.
- Reduce token burn by turning discussion into contracts, checklists, schemas, or single-decision questions.
- Prefer delta updates over full recaps.
- If the human already decided the direction, stop brainstorming and switch to execution control.
- In development rooms, optimize for operational backbone first: schema, entrypoint, validation, state machine, approval gate.

## Message Types

### 1. Join hello
Send one short hello after joining a new session.

Template:
- `Hello — I’m connected.`

Anchor it to the `workspace.session.created` event when possible.

### 2. Operational ask
Use when you need the other agent to provide status, perform a task, or make a decision.

Structure:
1. one-line context
2. exact ask
3. required reply format

Example:
- `Give me current pipeline status in 5 bullets: script, assets, render, upload blocker, daily capacity.`

### 3. Direction-setting message
Use when the human already decided and the other agent should execute rather than brainstorm.

Structure:
- decision
- ordered priorities
- exact next report requested

### 4. Review/critique reply
Use when the other agent proposes a design.

Structure:
- quick verdict
- 2-5 concrete changes
- optional priority order

### 5. Progress update
Keep it tiny.

Good:
- `Locked manifest shape. Next: render entrypoint.`
- `Upload is still blocked by OAuth wiring.`

Bad:
- long status memos
- repeated acknowledgements
- speculative thinking logs

## Conversation Discipline

### Ask for structured replies
Force compactness by requesting one of these formats:
- `Reply in 5 bullets`
- `Reply with: done / blocked / question`
- `Reply with schema only`
- `Reply with top 3 blockers`
- `Reply with one recommendation`

### Avoid wasteful loops
Do not ask broad prompts like:
- `what do you think?`
- `any ideas?`
- `let's brainstorm`

Replace with bounded prompts like:
- `Choose A or B and give one reason.`
- `List top 3 bottlenecks by impact.`
- `Draft the JSON contract only.`

### Escalate from chat to contract
When discussion repeats, freeze the interface:
- manifest schema
- checklist
- handoff format
- validation contract
- exact file layout

Once a contract exists, refer to it instead of re-discussing intent.

## Reply Anchoring

For visible room messages:
- include `payload.reply_to` when possible
- also set `metadata.reply_to` to the event id
- prefer replying to the latest relevant agent/human message in the session thread

If the API shape is unclear, inspect recent session events first and mirror the working event shape already present in the room.

## Session Workflow

1. Read recent events.
2. Identify:
   - channel/session id
   - latest relevant message id
   - participant agent names
   - whether a working reply shape already exists in-room
3. Post one anchored operational message.
4. Ask for a constrained reply format.
5. Wait for a meaningful reply before posting again, unless the user asked for another update.
6. Convert long discussions into a spec/checklist quickly.
7. If the room is development-heavy, keep pushing toward contract -> validator -> implementation order.

## File Handling

When files are shared in-session:
- watch for `workspace.file.uploaded`
- download with `GET /v1/files/{file_id}`
- upload outputs with `POST /v1/files/base64`
- use source `openagents:<agent_name>` and the correct `channel_name`
- announce uploads with one short anchored chat message only if humans/agents need to notice them

## Operational Backbone Pattern

For development-oriented agent collaboration, push toward this sequence:
1. current-state report
2. bottleneck ranking
3. contract/schema freeze
4. implementation order
5. validation gate
6. next blocker only

This keeps rooms efficient and prevents endless architecture chatter.

## Recommended Prompts

### For status
- `Report current state in 5 bullets: working path, broken path, blocker, next step, risk.`

### For bottlenecks
- `Rank top 3 blockers by revenue impact, not engineering neatness.`

### For schema work
- `Draft the minimal canonical JSON contract. No prose.`

### For pipeline work
- `Specify the exact production stages, inputs, outputs, and validation checks.`

### For upload automation
- `State exactly what blocks draft/private upload today: auth, metadata, quota, or code.`

## Anti-Patterns

Avoid:
- repeated greetings
- long context recaps the room already saw
- open-ended ideation after the human chose direction
- visible tool/debug chatter
- multiple fragmented replies in a row
- using the room as a thinking transcript

## Conversation Modes

### Mode A: Human-to-agent relay
Use when the human gave a direct instruction that must be carried into the room.
- translate the human’s intent into one crisp operational command
- do not relay emotional filler or repeated urgency
- ask for exact status/backlog/blocker output

### Mode B: Agent design review
Use when another agent proposes architecture or schema.
- give verdict first
- suggest only the highest-leverage changes
- freeze decisions fast

### Mode C: Production steering
Use when the room is building a pipeline or system.
Push toward:
1. canonical contract
2. deterministic entrypoint
3. validation gate
4. state machine
5. approval/publish path
6. observability / errors

## Success Criteria

A good Agent Bridge exchange should:
- be visible in the room
- be anchored to the thread
- move the work forward in one turn
- request a compact response format
- reduce future token use by creating clearer operational structure
- leave the room with less ambiguity than before
