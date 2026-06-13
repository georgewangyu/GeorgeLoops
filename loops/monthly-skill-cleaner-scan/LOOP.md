---
id: "monthly-skill-cleaner-scan"
name: "Monthly Skill Cleaner Scan"
status: "active"
owner: "George"
cadence: "first Saturday monthly gate"
runtime: "codex-cron"
automation_id: "monthly-skill-cleaner-scan"
risk: "medium"
---

# Monthly Skill Cleaner Scan

## Purpose

Keep the skill layer useful by controlling duplicates, stale roots, verbose
instructions, and context-budget creep.

The runtime schedule is weekly because the Codex App automation schema supports
weekly/hourly schedules. The prompt includes a first-Saturday gate, so non-monthly
runs should no-op.

## Inputs

- `<home>/.codex/skills`
- `<home>/.agents/skills`
- `<workspace>/georgeskills/skills`
- Recent usage evidence when accessible

## Workflow

1. If today is not the first Saturday of the month, report a no-op.
2. Inspect skill roots and recent usage evidence.
3. Identify duplicate names, overlapping descriptions, stale roots, unused
   skills, verbose instructions that should move into scripts, and protected
   skills that should remain.
4. Produce keep/compact/disable/delete recommendations with evidence.

## Outputs

A prompt-budget and skill-maintenance report.

## Guardrails

- Do not edit files.
- Do not delete directories.
- Do not change skill roots.
- Do not commit.
- Do not take public actions.
- Include an explicit "do not delete automatically" warning.

## Why It Is Useful

Skills are powerful until they become noise. This loop keeps the assistant's
tooling surface from growing into a context-budget tax.

## Verifier

Recommendations separate safe compaction from risky deletion, and each proposed
change includes evidence.
