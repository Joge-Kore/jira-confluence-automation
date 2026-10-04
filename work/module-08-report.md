# Module 08 Completion Report

## Tracked Files
.gitignore
README.md
WEEKLY_STATUS_REPORT_TEMPLATE.md
calculator.py
main.py
project_spec.md

## Spec Commit History
0e46e71 (HEAD -> master) Module-8 Clarifying Requirements

## project_spec.md Contents
# Weekly Status Report Generator - Technical Specification

## 1. Overview
Build a local, manually triggered report generator that pulls data from a single Jira Scrum board and produces a weekly stakeholder status report for a Project Manager or Scrum Master managing a 10-person project team.

## 2. Primary User
- Role: Project Manager / Scrum Master
- Team Size: 10 people
- Project Context: One project, one Jira Scrum board
- Primary Audience: Client Manager

## 3. Objectives
- Generate a stakeholder-friendly weekly status report from Jira sprint data.
- Reduce manual effort in reviewing board activity and formatting updates.
- Provide a balanced summary covering delivery progress, team execution, and risk visibility.

## 4. In Scope for Version 1
- Pull data from one Jira Scrum board.
- Use active sprint data only.
- Run manually on demand as a local desktop script.
- Output the report in Markdown.
- Produce email-ready content that can be copied into stakeholder communication.

## 5. Out of Scope for Version 1
- Confluence publishing
- Scheduled automation
- Multi-board aggregation
- Portfolio-level reporting
- Advanced trend analytics across multiple sprints

## 6. Jira Source Configuration
- Board Type: Scrum Board
- Jira Project / Board Identifier: EPMICMPMD
- Scope of Extraction: Active sprint only

## 7. Required Jira Data Fields
- Issue key
- Summary
- Status
- Assignee
- Story points
- Due date
- Issue type

## 8. Report Sections
The generated report must include these sections in bullet-point format:
- Completed issues
- In-progress items
- Blockers
- Next sprint goals
- Team capacity or availability

## 9. Inclusion and Classification Rules
- Completed issues: issues in the active sprint that are in a completed/done status.
- In-progress items: issues in the active sprint that are not done and are actively being worked.
- Blockers: issues identified by a combination of blocked status, blocker label, blocked-by links, or manual notes.
- Next sprint goals: a placeholder or generated section summarizing expected goals for the next sprint based on available Jira issues or user-provided notes.
- Team capacity or availability: a summary section intended for manual input unless capacity data is available from Jira or an auxiliary source.

## 10. Output Requirements
- File format: Markdown
- Secondary use: Email-ready text
- Tone: Balanced summary
- Formatting: stakeholder-readable bullet points with minimal technical noise

## 11. Functional Requirements
- Accept Jira connection settings for the target board.
- Query the active sprint for board issues.
- Extract the required issue fields.
- Classify issues into the required report sections.
- Generate a Markdown report using a consistent template.
- Keep report output concise and ready for stakeholder sharing.
- Allow manual editing of the generated output before distribution.

## 12. User Workflow
1. User runs the script locally on demand.
2. Script connects to Jira and fetches active sprint issues from the specified Scrum board.
3. Script classifies issues into completed, in-progress, blockers, and candidate next-sprint items.
4. Script generates a Markdown weekly status report.
5. User reviews and optionally edits the content before sharing with stakeholders.

## 13. Non-Functional Requirements
- Simple local execution without admin-level infrastructure dependencies.
- Readable output suitable for non-engineering stakeholders.
- Fast execution suitable for weekly reporting use.
- Maintainable structure so sections or rules can be adjusted later.

## 14. Assumptions
- Jira is the system of record for sprint work.
- The active sprint contains the relevant work for the weekly report.
- Some sections, especially team capacity and parts of next sprint goals, may require manual augmentation in version 1.
- Authentication approach is not yet specified and will be defined during implementation planning.

## 15. Open Questions
- Exact Jira authentication method: API token, SSO-compatible flow, or service credential.
- Exact mapping of Jira statuses to Done and In Progress categories.
- Whether next sprint goals should be generated from the backlog, the next planned sprint, or entered manually.
- Whether team capacity should come from Jira fields, a separate staffing source, or manual notes.

## 16. Version 1 Success Definition
Version 1 is successful if the Project Manager or Scrum Master can run a local script against the EPMICMPMD Scrum board and receive a concise Markdown weekly report for the Client Manager containing completed issues, in-progress items, blockers, next sprint goals, and team capacity notes with minimal manual reformatting.
