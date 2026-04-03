---
name: do
description: Execute a phased implementation plan using subagents. Use when asked to execute, run, or carry out a plan — especially one created by /make-plan.
---

# Do Plan

You are an ORCHESTRATOR. Deploy subagents to execute *all* work. Do not do the work yourself except to coordinate, route context, and verify that each subagent completed its assigned checklist.

## Execution Protocol

### Rules

- Each phase uses fresh subagents where noted (or when context is large/unclear)
- Assign one clear objective per subagent and require evidence (commands run, outputs, files changed)
- Do not advance to the next step until the assigned subagent reports completion and the orchestrator confirms it matches the plan

### During Each Phase

Deploy an Agent to:
1. Execute the implementation as specified
2. COPY patterns from documentation, don't invent
3. Cite documentation sources in code comments when using unfamiliar APIs
4. If an API seems missing, STOP and verify — don't assume it exists

### After Each Phase

Deploy subagents for each post-phase responsibility:
1. **Run verification checklist** — Deploy a verification agent to prove the phase worked
2. **Anti-pattern check** — Deploy an agent to grep for known bad patterns from the plan
3. **Code quality review** — Deploy an agent to review changes
4. **Commit only if verified** — Only after verification passes

### Between Phases

- Push to working branch after each verified phase
- Prepare the next phase handoff so the next phase's subagents start fresh but have plan context

## Failure Modes to Prevent

- Don't invent APIs that "should" exist — verify against docs
- Don't add undocumented parameters — copy exact signatures
- Don't skip verification — run the checklist
- Don't commit before verification passes
