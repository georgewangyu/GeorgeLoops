---
id: "refactor-until-architecture-settles"
name: "Refactor Until Architecture Settles"
status: "reference"
owner: "George"
runtime: "manual"
risk: "medium"
source: "Peter Steinberger X reply, 2026-06-12; Matthew Berman X resurfacing; Forward Future Loop Library architecture satisfaction loop"
---

# Refactor Until Architecture Settles

## Purpose

Give an agent a bounded architecture-refactor objective that continues until
the design is coherent, real user-facing behavior has been exercised, and the
result is reviewable.

This is a goal recipe, not an active loop or automation.

## Prompt

```text
/goal refactor [project-or-module] until the architecture is coherent and I would be happy maintaining it.

Constraints:
- Preserve existing behavior unless I explicitly ask for behavior changes.
- Keep a running progress artifact inside the target repo at [progress-artifact-path].
  Prefer an existing docs/design/investigations/issues/progress folder; if none
  exists, propose the smallest durable repo-owned location before editing.
- After each significant step, run live verification that exercises the real workflow end to end.
- For UI work, live verification must include the strongest available browser,
  app, or computer-use check, not just static inspection or unit tests.
- Run an independent autoreview before considering the work done.
- Commit and push are allowed when the user has asked for a shipped/pushed
  result and the final diff is low-risk, reviewable, verified, and free of
  secrets or unrelated changes. Ask for explicit approval before merge,
  publish, delete, move, or any risky/destructive commit.

Stop when:
- the architecture is simpler or more coherent than the starting point,
- the relevant live workflow has been verified with evidence,
- the UI surface still works across the important states and viewports, if applicable,
- remaining risks are listed clearly, and
- the diff is small enough to review.
```

## When To Use

- A module works but has grown hard to reason about.
- The desired architecture is directional rather than fully specified.
- Live behavior matters more than static cleanup.
- The agent can run tests or operate the app enough to catch regressions.
- A frontend or full-stack project needs a real UI pass while the architecture
  is being simplified.

## Inputs

- Target project or module
- Existing tests and manual verification path
- Current architecture notes, if any
- Important UI routes, states, or user journeys, if applicable
- A repo-owned progress artifact path, such as:
  - `<project>/docs/refactors/YYYY-MM-DD-<project>-architecture-refactor.md`
  - `<project>/docs/design/YYYY-MM-DD-<module>-refactor.md`
  - `<project>/investigations/YYYY-MM-DD-<module>-architecture.md`
  - `<project>/progress/YYYY-MM-DD-<module>-refactor.md`

## Workflow

1. Read the target code and write the current architecture in the progress
   artifact.
2. Propose the smallest refactor path that improves coherence.
3. Make one meaningful change at a time.
4. After each significant change, verify with tests and live app/browser/computer
   use when relevant.
5. For UI work, capture the states checked: routes, viewport sizes, core flows,
   loading/error/empty states, and any interaction that could have regressed.
6. Autoreview the diff for regressions, overreach, and leftover complexity.
7. Stop with a concise summary of what changed, what was verified, and what
   still feels architecturally weak.

## Guardrails

- Do not treat "happy with the architecture" as permission for open-ended
  rewrites.
- Do not expand scope beyond the named project or module.
- Low-risk commit/push is allowed after verification when the user has asked
  for a shipped/pushed result. Before doing it, confirm the diff is scoped,
  public-safe, secret-free, and does not include unrelated work.
- Ask for explicit approval before merging, publishing, deleting, moving files,
  rewriting history, force-pushing, or committing risky/destructive changes.
- Do not delete data, publish, email, or change external state.
- If live verification is unavailable, stop and report the verification gap.
- Do not put the only progress record in `/tmp`, chat history, or another
  disposable location.
- Do not count the goal complete if the UI was affected but only code-level
  tests were run.
- Do not let "happy with the architecture" override concrete regressions,
  failing checks, or a diff that is too broad to review.

## Completion Criteria

- The architecture is simpler to explain than at the start.
- Behavior-preserving checks pass.
- The important user-facing workflow has been live-tested with browser/app or
  computer-use evidence when applicable.
- UI routes, states, and responsive layouts touched by the refactor have been
  checked explicitly.
- The repo-owned progress artifact records the target architecture, decisions,
  verification evidence, remaining risks, and next action.
- Autoreview does not identify a blocking regression.
- If a commit/push is part of the user-requested outcome, the pushed diff is
  low-risk, scoped, verified, and public-safe.
- Remaining tradeoffs are explicit.

## Notes

Found again from Matthew Berman's recent X post resurfacing Peter Steinberger's
June 12, 2026 X reply and the Forward Future Loop Library entry "The
architecture satisfaction loop":

- Matthew Berman X source: `https://x.com/MatthewBerman/status/2067742219235471419`
- Peter Steinberger X source: `https://x.com/steipete/status/2065357277880877413`
- Loop Library source:
  `https://signals.forwardfuture.ai/loop-library/loops/architecture-satisfaction-loop/`

The key pattern is that architecture refactoring should be paired with live
testing, progress tracking, and independent review rather than treated as a
one-shot prompt. Peter's follow-up also clarifies that live testing can mean
computer use, browser use, app interaction, keys, or other tools needed to fully
verify behavior end to end.

The original public loop suggests tracking progress in `/tmp/refactor-*`. For
GeorgeLoops, adapt that part: progress belongs in a durable repo artifact, near
the design docs, investigations, issue notes, or progress logs that future
sessions will actually reload.
