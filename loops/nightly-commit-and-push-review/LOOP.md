---
id: "nightly-commit-and-push-review"
name: "Nightly Commit and Push Review"
status: "active"
owner: "George"
cadence: "daily 9 PM"
runtime: "codex-cron"
automation_id: "nightly-commit-and-push-review"
risk: "high"
---

# Nightly Commit and Push Review

## Purpose

Review dirty workspace repositories at night, make defensible local commits,
and push only changes that pass an explicit unattended-publication gate.

This loop exists because George often creates useful work across many sibling
repos during the day. Without a nightly review pass, local changes and
unpushed commits pile up until the workspace becomes hard to reason about.

## Trigger

Runs daily at 9 PM local time.

## Inputs

- Top-level workspace git repositories
- Staged, unstaged, and untracked files
- Local branch and upstream status
- Local commits not yet pushed to their upstream
- Later-queue orchestration rules for push/no-push routing

## Workflow

1. Scan every top-level git repository in the workspace.
2. Identify staged, unstaged, untracked, and unpushed work.
3. Inspect changed files and group related work into sensible local commits
   only when the grouping is defensible.
4. Leave ambiguous files, generated artifacts, suspicious files, failed checks,
   or mixed unrelated changes for owner review.
5. Classify unpushed commits using unattended-publication routing:
   - `autonomous-push`
   - `needs-owner`
   - `waiting`
6. Push only `autonomous-push` candidates where upstream, validation,
   sensitivity, branch, and public-safety checks are clean.
7. Report commits created, pushes completed, and anything needing review.

## Outputs

- Local commits for clearly grouped changes.
- Optional pushes for `autonomous-push` candidates only.
- Nightly review report with repo, branch, commit, push, and blocked-item
  receipts.

## Guardrails

- Do not push if a repo has missing upstream, divergent branches, failed
  checks, public/private ambiguity, secret-looking files, generated binary
  uncertainty, or mixed unrelated work.
- Do not force-push.
- Do not hide uncertainty; route it to owner review.
- Do not treat "dirty" as automatically bad. Some work should remain uncommitted
  until George reviews it.
- Keep private and public repository boundaries explicit.

## Verifier

The loop is successful when clean work is committed or pushed with receipts,
and risky or ambiguous work is explicitly left for owner review instead of
being swept into a bad commit.

## Promotion Notes

Already active, but high risk. Keep improving the push gate before expanding
what counts as autonomous.
