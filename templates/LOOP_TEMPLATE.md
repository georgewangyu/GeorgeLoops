---
id: "<loop-id>"
name: "<Human Name>"
status: "idea|testing|active|retired"
owner: "<owner>"
cadence: "<manual|daily|weekly|monthly|event-triggered>"
runtime: "<manual|codex-cron|codex-heartbeat|script>"
automation_id: ""
risk: "low|medium|high"
---

# <Human Name>

## Purpose

What recurring mess, opportunity, or decision this loop handles.

## Trigger

When this loop should run.

## Inputs

- Source 1
- Source 2

## Workflow

1. Inspect the inputs.
2. Produce a bounded shortlist.
3. Attach evidence and a recommended next action.

## Outputs

- Report location or response format.
- Maximum number of recommendations.

## Guardrails

- Do not take public actions.
- Do not delete, move, or publish anything unless this loop explicitly includes
  a human approval gate.

## Verifier

What proves the loop produced useful output.

## Promotion Notes

What evidence is needed before this loop becomes more automated.
