---
id: "biweekly-sprint-retro-and-next-sprint-planning"
name: "Biweekly Sprint Retro and Next Sprint Planning"
status: "active"
owner: "George"
cadence: "every 2 weeks Sunday 8 PM"
runtime: "codex-cron"
automation_id: "biweekly-sprint-retro-and-next-sprint-planning"
risk: "medium"
---

# Biweekly Sprint Retro and Next Sprint Planning

## Purpose

Close the current sprint with a real retrospective and seed the next sprint so
Monday has an operating surface.

This loop converts daily summaries, metrics, sprint plans, and open reflection
questions into a retro artifact plus a next-sprint plan. It should make the
end of a sprint concrete without pretending to know subjective answers George
has not provided.

## Trigger

Runs every two weeks on Sunday at 8 PM local time.

## Inputs

- GeorgeRepo journal routing instructions
- Sprint retro workflow docs
- Current and previous sprint plan files
- Daily summaries inside the sprint window
- Daily and sprint metrics when useful
- Sprint allocation report output
- Current day's daily summary

## Workflow

1. Determine the current local date and identify the sprint window ending or
   just ended.
2. Read the relevant sprint plan, previous retro, daily summaries, metrics, and
   reflection files.
3. Run the sprint allocation report for the window.
4. Draft or update the sprint retro with goal achievement, metrics, domain
   allocation, wins, recurring friction, decisions, next-sprint adjustments,
   open questions, and final judgment.
5. If George's subjective interview answers are missing, add clear open
   reflection questions instead of fabricating them.
6. Seed the next sprint plan if one does not exist; otherwise update only the
   opening planning sections and preserve user-authored content.
7. Add a concise milestone to the current daily summary.
8. Run a diff check and return a review bundle.

## Outputs

- Sprint retro artifact.
- Next sprint plan artifact or updated planning section.
- Current-day daily summary milestone.
- Review bundle with sprint window, artifact paths, metrics headline, top
  process changes, unanswered questions, and validation result.

## Guardrails

- Do not fabricate subjective reflections.
- Do not overwrite user-authored sprint content.
- Do not edit unrelated repo files.
- Do not auto-push or take public actions.
- Preserve uncertainty about implicit sprint boundaries.

## Verifier

The loop is useful when it produces a reviewable retro, a concrete next-sprint
starting surface, and a short list of unanswered human reflection questions.

## Promotion Notes

Already active. Improve by making sprint boundary detection more explicit and
keeping next-sprint goals limited to a small number George can actually act on.
