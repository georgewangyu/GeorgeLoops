---
id: "refactor-until-architecture-settles"
name: "Refactor Until Architecture Settles"
status: "reference"
owner: "George"
runtime: "manual"
risk: "medium"
source: "Peter Steinberger X reply, 2026-06-12"
---

# Refactor Until Architecture Settles

## Purpose

Give an agent a bounded architecture-refactor objective that continues until
the design is coherent, live-tested, and reviewable.

This is a goal recipe, not an active loop or automation.

## Prompt

```text
/goal refactor [project-or-module] until the architecture is coherent and I would be happy maintaining it.

Constraints:
- Preserve existing behavior unless I explicitly ask for behavior changes.
- Keep a running progress note at [progress-note-path].
- After each significant step, run live verification that exercises the real workflow.
- Use computer/browser/app views when needed to verify the actual user-facing behavior.
- Run an autoreview before considering the work done.
- Do not commit, merge, publish, delete, or move anything without explicit approval.

Stop when:
- the architecture is simpler or more coherent than the starting point,
- the relevant live workflow has been verified,
- remaining risks are listed clearly, and
- the diff is small enough to review.
```

## When To Use

- A module works but has grown hard to reason about.
- The desired architecture is directional rather than fully specified.
- Live behavior matters more than static cleanup.
- The agent can run tests or operate the app enough to catch regressions.

## Inputs

- Target project or module
- Existing tests and manual verification path
- Current architecture notes, if any
- A progress-note path such as `<workspace>/tmp/refactor-<project>.md`

## Workflow

1. Read the target code and write the current architecture in the progress note.
2. Propose the smallest refactor path that improves coherence.
3. Make one meaningful change at a time.
4. After each significant change, verify with tests and live app/browser/computer
   use when relevant.
5. Autoreview the diff for regressions, overreach, and leftover complexity.
6. Stop with a concise summary of what changed, what was verified, and what
   still feels architecturally weak.

## Guardrails

- Do not treat "happy with the architecture" as permission for open-ended
  rewrites.
- Do not expand scope beyond the named project or module.
- Do not commit or merge without explicit approval.
- Do not delete data, publish, email, or change external state.
- If live verification is unavailable, stop and report the verification gap.

## Completion Criteria

- The architecture is simpler to explain than at the start.
- Behavior-preserving checks pass.
- The important user-facing workflow has been live-tested when applicable.
- Autoreview does not identify a blocking regression.
- Remaining tradeoffs are explicit.

## Notes

Inspired by Peter Steinberger's `/goal` refactor advice on X: architecture
refactoring should be paired with live testing, progress tracking, and
autoreview rather than treated as a one-shot prompt.
