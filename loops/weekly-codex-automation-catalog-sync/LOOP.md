---
id: "weekly-codex-automation-catalog-sync"
name: "Weekly Codex Automation Catalog Sync"
status: "testing"
owner: "George"
cadence: "weekly Saturday 9 AM"
runtime: "codex-cron"
automation_id: "weekly-codex-automation-catalog-sync"
risk: "low"
---

# Weekly Codex Automation Catalog Sync

## Purpose

Keep GeorgeLoops aligned with the Codex automations and reusable goal recipes
that are actually being created.

GeorgeLoops should not be only an idea board. If a Codex automation is running
on a schedule, or a recent `/goal` pattern proved useful enough to reuse, this
loop checks whether it has a matching loop or goal doc and adds the missing
catalog entry when the source evidence is clean enough.

## Trigger

Run weekly on Saturday morning after the other weekly Codex automation reports
have had time to land.

## Inputs

- Codex App automation registry or current automation listing
- Recent Codex automation creation/update records from the last seven days
- Recent completed Codex `/goal` runs or goal-like prompts from the last seven
  days
- `<workspace>/GeorgeLoops/loops/`
- `<workspace>/GeorgeLoops/goals/`
- `<workspace>/GeorgeLoops/README.md`
- `<private-repo>/journal/summaries/`

## Workflow

1. List current Codex automations and identify any new or changed scheduled
   automations from the last seven days.
2. Review recent completed `/goal` runs and identify goal recipes that were
   useful, reusable, and not already captured in `goals/`.
3. Compare the source records against the GeorgeLoops catalog:
   - scheduled automation should map to `loops/<loop-id>/LOOP.md`
   - reusable unscheduled objective should map to `goals/<goal-id>/GOAL.md`
4. For each missing item, classify it as one of:
   - `auto-add`: enough evidence exists to create a public-safe doc
   - `needs-review`: useful but missing schedule, verifier, or boundaries
   - `skip`: one-off, private, risky, or not reusable
5. For `auto-add` items, create the minimal loop or goal doc, update the
   README catalog table, and keep status at `testing` until the item has
   produced useful output more than once.
6. Run the public-safety scan and include the result in the final report.
7. Return a short sync report listing added items, review-needed items, skips,
   and any blocked registry access.

## Outputs

- Local GeorgeLoops doc updates for `auto-add` items.
- A concise sync report with at most ten total items.
- Public-safety scan result.

## Guardrails

- Do not create, delete, pause, or edit Codex App automations.
- Do not invent automation ids, schedules, or completion evidence.
- Do not add private paths, private URLs, credentials, account identifiers, or
  raw transcript excerpts to GeorgeLoops.
- Do not add goals that are only one-off tasks.
- Do not commit or push without explicit human approval.
- If source evidence is incomplete, produce a `needs-review` report item
  instead of creating a doc.

## Verifier

The loop is successful when every new Codex automation from the review window
is either represented in GeorgeLoops or explicitly listed as skipped or
needs-review, and the public-safety scan returns no real leaks.

## Promotion Notes

Promote from `testing` to `active` after three runs where the sync either adds
useful catalog entries or correctly reports that no catalog changes are needed.
