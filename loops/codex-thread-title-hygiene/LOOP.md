---
id: "codex-thread-title-hygiene"
name: "Codex Thread Title Hygiene"
status: "active"
owner: "George"
cadence: "daily noon"
runtime: "codex-cron"
automation_id: "codex-thread-title-hygiene"
risk: "medium"
---

# Codex Thread Title Hygiene

## Purpose

Keep Codex thread titles durable enough that recent and pinned work can be
found again.

This loop reviews pinned threads and recent Codex threads, skips titles that
are already specific, and renames only vague or stale titles when the better
title is high-confidence.

## Trigger

Runs daily at noon local time.

## Inputs

- Pinned Codex thread list
- Latest recent Codex thread list
- Thread title previews
- Small recent-turn samples only when a title needs inspection
- `codex-thread-hygiene-ops` skill rules

## Workflow

1. Review the pinned and recent thread list previews.
2. Skip titles that already follow a durable pattern such as
   `Project or Domain: Concrete Task`.
3. Treat null, default, vague, overly broad, colonless, or stale-looking titles
   as rename candidates.
4. Read thread details only for candidate titles, using the smallest recent
   sample that can support a decision.
5. Rename only when the new title is high-confidence and uses the pattern
   `Project or Domain: Concrete Task or Outcome`.
6. Report renamed titles, skipped-good titles, unresolved failures, and future
   scope recommendations.

## Outputs

- Renamed Codex thread titles when high-confidence.
- Hygiene report with action counts, skips, failures, and recommendations.

## Guardrails

- Do not change pin or archive state.
- Do not include raw tool outputs unless absolutely necessary.
- Do not rename titles that are already specific and stable.
- Do not guess a durable title from weak evidence.

## Verifier

The loop is useful when vague recent/pinned titles are reduced and already-good
titles are skipped without unnecessary thread reads.

## Promotion Notes

Already active. Watch for over-renaming; if false positives appear, tighten the
candidate criteria before increasing scope.
