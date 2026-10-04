# Module 10 Completion Report

## Instruction Files
```text

    Directory: C:\Users\JogeswaraKore\OneDrive - 
    EPAM\My_Workspace\mgr.ai.ws\hello-genai\work\module03-task\instructions


Mode                 LastWriteTime         Length Name                         
----                 -------------         ------ ----                         
-a---l        02-10-2026     22:18           1475 classify-jira-issues.agent.md
-a---l        02-10-2026     21:44            211 create-status-report.agent.md
-a---l        02-10-2026     21:59           1499 creating-instructions.agent.m
                                                  d                            
-a---l        02-10-2026     22:18           1375 generate-jira-report-sections
                                                  .agent.md                    
-a---l        02-10-2026     22:18           1453 main.agent.md                


PS C:\Users\JogeswaraKore\OneDrive - EPAM\My_Workspace\mgr.ai.ws\hello-genai\wor
k\module03-task> 
```

## main.agent.md Contents
```markdown
# Instructions Catalog

Each entry below is an instruction file with a one-line description.
Optional sub-fields after `+`:
- `Keywords` — trigger words or phrases that should load this instruction.
- `Target` — file glob patterns that make the instruction relevant.
- `Exceptions` — edge cases or clarifications.

---


- [`./creating-instructions.agent.md`](./creating-instructions.agent.md) — Create or update project instructions, catalogs, and Copilot wrappers for reusable workflows.
	+ Keywords: create instruction, update instruction, bootstrap instructions, configure copilot instructions, prompt wrapper


- [`./create-status-report.agent.md`](./create-status-report.agent.md) — Generate weekly status reports with fixed sections, concise bullets, and professional tone.
	+ Keywords: status report, weekly update, accomplishments, blockers, next week

- [`./classify-jira-issues.agent.md`](./classify-jira-issues.agent.md) — Classify sprint issues into completed, in-progress, blocker, and next-sprint candidate groups for reporting.
	+ Keywords: classify jira issues, report categories, blockers, in progress, done, next sprint

- [`./generate-jira-report-sections.agent.md`](./generate-jira-report-sections.agent.md) — Turn classified Jira issue data into stakeholder-ready Markdown report sections.
	+ Keywords: generate jira report, markdown sections, stakeholder update, completed issues, sprint report
```

## Sample Instruction
- File: classify-jira-issues.agent.md
- Contents:
```markdown
---
description: Classify Jira sprint issues into report groups using consistent status and field rules
---
- Input format:
  + Accept a list of Jira issues for one sprint.
  + Require these fields per issue: `key`, `summary`, `status`, `assignee`, `story_points`, `due_date`, `issue_type`.
  + Allow missing optional fields, but keep the issue in the dataset.
- Processing steps:
  + Normalize status names before classification.
  + Map each issue into exactly one group: `completed`, `in_progress`, `blocker`, or `next_sprint_candidate`.
  + Treat explicit blocked states, blocker labels, or dependency flags as `blocker`.
  + Treat done or closed states as `completed`.
  + Treat active working states as `in_progress`.
  + Treat work not planned for the current sprint but relevant for follow-up as `next_sprint_candidate`.
  + Preserve the original issue fields in the classified result.
  + Record assumptions when status names do not match expected values.
- Output format:
  + Return a Markdown-friendly structure grouped by `completed`, `in_progress`, `blocker`, and `next_sprint_candidate`.
  + Keep issue entries ordered consistently within each group.
  + Include enough issue detail to support direct report generation.
- Constraints:
  + Do not place one issue in multiple groups.
  + Do not invent missing Jira values.
  + Keep the grouping rules consistent across runs.
  + Prefer deterministic mapping over subjective interpretation.
```