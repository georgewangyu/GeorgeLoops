---
id: "wake-codex-repo-maintenance-loop"
name: "Wake Codex Repo Maintenance Loop"
status: "idea"
owner: "George"
cadence: "manual only"
runtime: "manual"
automation_id: ""
risk: "high"
source: "Peter Steinberger X post, 2026-06-11"
---

# Wake Codex Repo Maintenance Loop

## Purpose

Capture the idea of a persistent orchestrator that periodically wakes Codex,
checks repo state, and directs work into reviewable threads.

This is a reference loop only. It is not active and should not be scheduled
without a separate approval pass.

## Trigger

Manual experiment only, when there is a repo with enough active issues, PRs, or
maintenance work to justify a short-lived orchestrator.

Do not run this as a background loop by default.

## Inputs

- Target repository or bounded set of repositories
- Issue and PR list
- Recent failing checks or review comments
- Repo-specific agent instructions
- Available verification commands

## Workflow

1. Wake on a short interval during an approved experiment window.
2. Inspect the target repo's current work queue.
3. Select one small task or thread that has clear verification.
4. Dispatch Codex to the relevant thread or worktree with the exact goal,
   guardrails, and verifier.
5. Require the worker thread to report status, diff summary, and verification.
6. Autoreview worker output before proposing any merge, commit, or public action.
7. Stop when the experiment window ends, cost limits are reached, or the queue
   no longer contains bounded tasks.

## Outputs

- Work queue triage summary
- Threads started or continued
- For each thread: status, changed files, verification, blockers, and next step
- Explicit list of actions that still require human approval

## Guardrails

- Do not run continuously without a defined timebox.
- Do not commit, merge, push, publish, email, delete, or move files without a
  human approval gate.
- Do not create unbounded work across many repos.
- Do not keep spawning workers when verification is missing.
- Track cost, runtime, and open threads so the loop can be stopped cleanly.

## Why It Is Useful

The interesting part is not the five-minute timer. The useful pattern is an
orchestrator that keeps repo maintenance moving while preserving reviewable
threads, verification gates, and human control.

## Verifier

The loop is useful only if it produces a small number of reviewable completed
or blocked threads, each with concrete verification and no hidden external
actions.

## Promotion Notes

Before this becomes anything beyond a reference idea, it needs:

- a one-repo dry run,
- a hard timebox,
- cost/rate limits,
- a clear stop condition,
- and a human approval gate for commits, merges, pushes, and public actions.
