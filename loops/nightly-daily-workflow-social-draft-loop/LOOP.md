---
id: "nightly-daily-workflow-social-draft-loop"
name: "Nightly Daily Workflow Social Draft Loop"
status: "testing"
owner: "George"
cadence: "daily 10 PM"
runtime: "codex-cron"
automation_id: "nightly-daily-workflow-social-draft-loop"
risk: "medium"
---

# Nightly Daily Workflow Social Draft Loop

## Purpose

Turn the day's journal, transcript, work, and market signal into ranked
LinkedIn/X candidate angles and one or two local draft files.

This loop is explicitly not a posting loop.

## Inputs

- Current day's GeorgeRepo daily summary
- Same-day transcript/work artifacts
- Relevant git work and local notes
- Available calendar/email/health context through the daily workflow
- Market/research signal when relevant
- Local social-media writing instructions

## Workflow

1. Run or refresh the standard end-of-day daily workflow context.
2. Read the day's objective signal and unresolved gaps.
3. Produce two to four public-writing candidates.
4. Draft the best one or two candidates into local markdown files under
   `<social-posts-dir>`.
5. Return a review bundle asking George to choose what to expand or post.

## Outputs

- Daily workflow status and gaps
- Candidate ranking
- Created draft file paths
- Recommended next choice
- Explicit note that posting is pending George approval

## Guardrails

- Do not post to LinkedIn or X.
- Do not use `lbot`, `xbot`, gist publication, email, or any public action.
- Do not fabricate subjective reflection if George has not provided it.

## Why It Is Useful

The loop tries to catch the day's useful thought while it is still warm. The
value is candidate generation and local drafting, not unattended publishing.

## Verifier

Drafts cite concrete source notes from the day and remain public-safe enough
for George to review quickly.
