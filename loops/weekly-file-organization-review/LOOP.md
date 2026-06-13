---
id: "weekly-file-organization-review"
name: "Weekly File Organization Review"
status: "active"
owner: "George"
cadence: "weekly Saturday 9 AM"
runtime: "codex-cron"
automation_id: "weekly-file-organization-review"
risk: "medium"
---

# Weekly File Organization Review

## Purpose

Review loose local files and identify what belongs in GeorgeRepo, what is
duplicate/noise, and what needs George's manual decision.

## Inputs

- `<home>/Downloads`
- `<home>/Documents`
- `<external-drive>` when mounted
- GeorgeRepo as the private destination map

## Workflow

1. List recent PDFs, DOCX, XLSX/CSV, images, videos, archives, and audio.
2. Compare filenames and hashes against likely GeorgeRepo destinations.
3. Group candidates by destination domain.
4. Return high-confidence move candidates, duplicates/noise candidates,
   ambiguous files, and large media clusters that deserve a separate pass.

## Outputs

A concise report with the top fifteen candidates total.

## Guardrails

- Do not move files.
- Do not delete files.
- Do not rename files.
- Do not edit files.
- Do not commit.
- Do not expose secret or banking details in the report.

## Why It Is Useful

The useful part is not automatic sorting. It is getting a short, evidence-backed
review list so file cleanup does not become a three-hour emotional excavation.

## Verifier

The report ends with the smallest safe next action George can approve.
