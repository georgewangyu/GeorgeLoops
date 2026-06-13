---
id: "georgerepo-cleanup-candidate-scan"
name: "GeorgeRepo Cleanup Candidate Scan"
status: "active"
owner: "George"
cadence: "every two weeks Saturday 9 AM"
runtime: "codex-cron"
automation_id: "georgerepo-cleanup-candidate-scan"
risk: "low"
---

# GeorgeRepo Cleanup Candidate Scan

## Purpose

Keep GeorgeRepo from slowly turning into a private operating-system junk drawer.
The loop does not clean automatically; it finds the smallest cleanup candidates
with evidence and verifiers.

## Inputs

- GeorgeRepo file tree
- Markdown docs and agent instructions
- Scripts and config files
- Detectable duplicated code/config
- Build, lint, or test friction when visible

## Workflow

1. Look for oversized files, duplicated code/config, stale docs, unclear test
   commands, unused dependencies, and agent instruction gaps.
2. Return at most three candidates.
3. For each candidate, include exact paths, risk, smallest next patch, and
   verifier.

## Outputs

A bounded cleanup report with at most three candidates.

## Guardrails

- Do not edit files.
- Do not commit.
- Do not run destructive commands.
- Do not change repo state.
- Do not take public actions.

## Why It Is Useful

Cleanup is only useful when it stays small. This loop turns "the repo is messy"
into three concrete, reviewable options.

## Verifier

Each candidate has an exact path and a plausible patch that can be completed in
one focused follow-up session.
