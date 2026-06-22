# GeorgeLoops

GeorgeLoops is George's catalog for recurring AI loops: scheduled checks,
maintenance scans, content-review passes, and workflow rituals that are useful
enough to run again.

The shape is inspired by `georgeskills`, but the unit is different:

- A **skill** is a reusable capability an agent can load on demand.
- A **loop** is a recurring operating pattern with a cadence, inputs, output,
  guardrails, and a verifier.
- A **goal** is a reusable objective recipe that can be handed to an agent or
  used inside a loop, but does not run on a schedule by itself.

Good loops are usually boring. They watch a narrow surface, produce a bounded
report, and make the next human decision easier.

## Public-Safety Rule

Loop docs should be generalizable enough to publish. Keep the concept,
cadence, guardrails, and verifier concrete, but avoid local machine details.

Use placeholders instead of sensitive or machine-specific values:

- `<workspace>` for the local workspace root
- `<private-repo>` for GeorgeRepo or another private operating repo
- `<home>` for a user's home directory
- `<external-drive>` for removable storage
- `<social-posts-dir>` for local draft output

George/GeorgeRepo language is allowed when it makes the loop easier to
understand. Absolute paths, credentials, emails, private account ids, and secret
filenames are not.

## Structure

```text
GeorgeLoops/
  AGENTS.md
  README.md
  goals/
    <goal-id>/
      GOAL.md
  loops/
    <loop-id>/
      LOOP.md
  templates/
    GOAL_TEMPLATE.md
    LOOP_TEMPLATE.md
```

## Goal Catalog

These are not active automations. They are reusable objective recipes to keep
around for future agent work.

| Goal | Status | Why It Exists |
|---|---|---|
| `refactor-until-architecture-settles` | reference | Captures the Peter Steinberger-style `/goal` pattern for architecture refactors with live UI/e2e testing, progress notes, and autoreview. |

## Loop Catalog

| Loop | Status | Cadence | Why It Exists |
|---|---|---:|---|
| `daily-morning-routine` | active, useful | daily 9 AM | Runs the start-of-day journal, alert, market-radar, and planning workflow. |
| `nightly-commit-and-push-review` | active, useful | daily 9 PM | Reviews dirty repos, commits defensible work, and pushes only gated autonomous candidates. |
| `codex-thread-title-hygiene` | active, useful | daily noon | Keeps recent and pinned Codex thread titles specific enough to find again. |
| `weekly-agent-loop-scan` | active, useful | weekly Saturday 9 AM | Finds high-signal new loop candidates from recent work. |
| `weekly-codex-automation-catalog-sync` | active, testing | weekly Saturday 9 AM | Keeps GeorgeLoops aligned with newly created Codex automations and reusable goal recipes. |
| `georgerepo-cleanup-candidate-scan` | active, useful | every 2 weeks Saturday 9 AM | Finds small repo cleanup candidates before the private repo drifts. |
| `cross-repo-pattern-propagation-scan` | active, useful | weekly Saturday 9 AM | Spots patterns that worked in one repo and may deserve propagation. |
| `biweekly-sprint-retro-and-next-sprint-planning` | active, useful | every 2 weeks Sunday 8 PM | Turns sprint history into a retro and a concrete next-sprint plan. |
| `monthly-skill-cleaner-scan` | active, useful | first Saturday monthly gate | Keeps skills and context budget from becoming an unusable pile. |
| `weekly-file-organization-review` | active, useful | weekly Saturday 9 AM | Reviews Downloads/Documents/external drive candidates without moving anything automatically. |
| `nightly-daily-workflow-social-draft-loop` | active, testing | daily 10 PM | Turns daily workflow signal into draft social angles without posting. |
| `monitor-ai-warehouse-and-wono` | active, testing | weekly Saturday 9 AM | Watches selected creator sources for reusable hook mechanics and ignition ideas. |
| `wake-codex-repo-maintenance-loop` | idea, reference | manual only | Captures Peter Steinberger's wake-Codex-every-few-minutes repo-maintenance loop without enabling it. |

## Design Rules

1. Start report-only.
2. Keep scope narrow enough that the result can be reviewed in minutes.
3. Name exact inputs and exact outputs.
4. Add a verifier before adding automation.
5. Add an approval gate before any action that changes external state.
6. Promote loops only after they are useful more than once.
7. Run the public-safety scan before pushing.

## Public-Safety Scan

Before publishing, run:

```bash
rg -n "(/Users/|/Volumes/|\\.env|\\.tokens|token|secret|password|api[_-]?key|[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,})" .
```

Expected result: no real secrets, no absolute local paths, and no private
emails. False positives like the word "token" in a generic warning should be
reviewed before pushing.
