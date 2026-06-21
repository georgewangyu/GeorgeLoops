---
id: "daily-morning-routine"
name: "Daily Morning Routine"
status: "active"
owner: "George"
cadence: "daily 9 AM"
runtime: "codex-cron"
automation_id: "daily-morning-routine"
risk: "low"
---

# Daily Morning Routine

## Purpose

Run George's start-of-day workflow with enough context to make the day easier
to choose, not just easier to summarize.

This loop prepares the daily summary, checks morning alerts, reads market and
builder signals, and routes the useful parts into planning, content ideas,
automation candidates, and project follow-ups.

## Trigger

Runs daily at 9 AM local time.

## Inputs

- Workspace routing instructions
- GeorgeRepo journal workflow docs
- Current day's daily summary
- Local morning brief helper output
- Configured X, GitHub, Product Hunt, YC / Launch HN, and video-watchlist
  sources
- Recent journal, health, calendar, and alert context when available

## Workflow

1. Load workspace and journal routing instructions.
2. Determine the current local date and create or update the daily summary.
3. Run the morning brief helper and surface alert/watch status before planning.
4. Run the expanded market radar pass across configured public sources.
5. Write detailed source sections for the useful X, GitHub, Product Hunt, and
   launch signals that are available.
6. Add a ranked signal-routing section:
   - ignition event candidates
   - skill or automation candidates
   - repos or posts to study
   - content ideas
   - personal project candidates
7. Translate the signal into practical planning implications and suggested
   priorities for the day.

## Outputs

- Updated daily summary sections for market radar, signal routing, and
  conversation milestones.
- Morning brief response with alerts, source reads, recommendations, blockers,
  and suggested priorities.

## Guardrails

- Do not post to public platforms.
- Do not expose credentials, private account ids, or raw private records.
- If a source is blocked, stale, or inaccessible, say so instead of filling in
  with guesses.
- Keep recommendations ranked and concrete; avoid turning the morning brief
  into a giant possibility cloud.

## Verifier

The run is useful when the daily summary has concrete morning context and the
final brief gives George a ranked plan, not just a digest.

## Promotion Notes

Already active. Improve by tightening stale-source detection and reducing any
source sections that stop producing decisions.
