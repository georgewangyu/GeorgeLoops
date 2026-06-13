---
id: "cross-repo-pattern-propagation-scan"
name: "Cross-Repo Pattern Propagation Scan"
status: "active"
owner: "George"
cadence: "weekly Saturday 9 AM"
runtime: "codex-cron"
automation_id: "cross-repo-pattern-propagation-scan"
risk: "low"
---

# Cross-Repo Pattern Propagation Scan

## Purpose

Find patterns that worked in one repo and may deserve to be copied into others.
This loop is for repo-shape hygiene: docs, startup instructions, verifier
commands, helper scripts, and conventions.

## Inputs

- Top-level Workspace git repositories
- Recent changes from the last fourteen days
- `AGENTS.md` / `AGENT.md`
- `README.md`
- `VISION.md` / `IMPROVEMENTS.md`
- `SKILL.md`
- Helper scripts and test/build command conventions

## Workflow

1. Identify source patterns changed recently.
2. Decide whether each pattern looks proven, not merely new.
3. List candidate target repos and explain what should change, what should be
   skipped, and what verifier would prove the propagation worked.
4. Return at most five candidates.

## Outputs

A cross-repo propagation shortlist.

## Guardrails

- Do not edit files.
- Do not commit.
- Do not change repo state.
- Do not take public actions.

## Why It Is Useful

George keeps discovering useful repo conventions one repo at a time. This loop
stops those improvements from staying trapped in whichever repo happened to get
attention first.

## Verifier

The report names a source pattern, target repos, skipped repos, and a concrete
verification command or check.
