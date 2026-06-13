# GeorgeLoops Agent Instructions

GeorgeLoops is George's catalog for recurring AI loops.

## Startup

Read in order:

1. `README.md`
2. Relevant `loops/<loop-id>/LOOP.md`
3. `templates/LOOP_TEMPLATE.md` when creating a new loop

## Editing Rules

- Keep each loop in `loops/<loop-id>/LOOP.md`.
- Keep each goal recipe in `goals/<goal-id>/GOAL.md`.
- Every loop should define purpose, trigger, cadence, inputs, workflow,
  outputs, guardrails, and verifier.
- Every goal should define purpose, prompt, when to use it, inputs, workflow,
  guardrails, and completion criteria.
- Goals are reusable prompt recipes, not scheduled automations. A goal may be
  used inside a loop, but it should not imply recurring execution by itself.
- Prefer report-only loops until they have been tested repeatedly.
- Do not add destructive actions such as moving files, deleting files, posting,
  emailing, or committing unless the loop has an explicit human approval gate.
- If a loop is backed by a Codex automation, record the automation id and
  schedule in the loop doc.
- Keep this repo focused on loop definitions and templates. Do not store social
  scripts, captions, or content drafts here.

## Boundary

- This repo documents loop design and observed usefulness.
- The Codex app automation registry remains the runtime source for scheduled
  runs until a loop is promoted into another runtime.
- Keep this repo public-safe by default: use placeholders such as
  `<workspace>`, `<private-repo>`, `<home>`, `<external-drive>`, and
  `<social-posts-dir>` instead of absolute local paths, credentials, account
  ids, emails, or private URLs.
- It is fine to keep George/GeorgeRepo language where it is part of the concept
  or storytelling. Do not include secrets or machine-specific identifiers.
