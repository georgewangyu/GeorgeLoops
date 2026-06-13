---
id: "<goal-id>"
name: "<Human Name>"
status: "idea|reference|tested|retired"
owner: "<owner>"
runtime: "<manual|agent-command|loop-embedded>"
risk: "low|medium|high"
source: ""
---

# <Human Name>

## Purpose

What objective this goal gives an agent.

## Prompt

```text
Copy-paste-ready goal prompt with placeholders like [project] or [scope].
```

## When To Use

- Situation where this goal is appropriate.

## Inputs

- Source 1
- Source 2

## Workflow

1. Inspect the relevant context.
2. Work toward the stated objective.
3. Verify progress after meaningful changes.
4. Stop with a concise report when completion criteria are met or blocked.

## Guardrails

- Do not take public actions.
- Do not delete, publish, email, or commit unless the goal explicitly includes
  a human approval gate.
- Keep state and progress notes in a reviewable artifact.

## Completion Criteria

What proves the goal is complete enough to stop.

## Notes

Any source attribution, caveats, or promotion notes.
