---
id: "weekly-agent-loop-scan"
name: "Weekly Agent Loop Scan"
status: "active"
owner: "George"
cadence: "weekly Saturday 9 AM"
runtime: "codex-cron"
automation_id: "weekly-agent-loop-scan"
risk: "low"
---

# Weekly Agent Loop Scan

## Purpose

Find new high-signal loop candidates from the last week of GeorgeRepo work.
This is the meta-loop: it notices when a repeated annoyance, workflow pattern,
or cleanup need is happening often enough to become its own loop.

## Inputs

- `<private-repo>/journal/summaries/`
- Recent git commits and changed files
- `<private-repo>/knowledge/ai-agents/`
- Recent reusable-skill references
- Changed `AGENTS.md`, `AGENT.md`, `README.md`, `VISION.md`,
  `IMPROVEMENTS.md`, `SKILL.md`, and scripts

## Workflow

1. Review the last seven days of journal, git, and workflow changes.
2. Identify at most five candidates across cross-repo propagation, repo cleanup,
   and skill/context-budget cleanup.
3. For each candidate, include evidence, recommended loop type, risk, verifier,
   and smallest next action.

## Outputs

A concise report with at most five loop candidates.

## Guardrails

- Do not edit files.
- Do not commit.
- Do not delete skills.
- Do not change repo state.
- Do not take public actions.

## Why It Is Useful

It converts repeated chaos into named maintenance systems. Instead of waiting
until the workspace feels messy, it asks whether the mess has become a pattern.

## Verifier

At least one candidate is specific enough that George can approve or reject the
next action in under five minutes.
