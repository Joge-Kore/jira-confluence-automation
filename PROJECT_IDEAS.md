# Project Ideas: Jira/Confluence Automation

## 1. Sprint Health & Risk Digest

**Problem it solves:** Managers often discover sprint risks (unassigned tickets, stalled blockers, scope creep) only during the sprint review, when it's too late to react. Manually checking Jira boards daily is time-consuming and easy to skip.

**What it does:** An automation that runs daily, scans the active sprint, and posts a summary (via email, Slack, or a Confluence page) highlighting at-risk items: tickets with no recent activity, unassigned high-priority issues, blocked tickets, and tickets added mid-sprint.

**Data needed:**
- Jira issue fields: status, assignee, priority, labels, last updated timestamp, sprint field, created date
- Sprint start/end dates (via Jira Agile/Scrum board API)
- Issue link types (to detect "blocked by" relationships)
- Historical sprint data (optional, for trend comparison)

## 2. Automated Release Notes Generator

**Problem it solves:** Compiling release notes from completed tickets is a manual, repetitive task that pulls time away from planning. It's also prone to missing tickets or including inconsistent descriptions.

**What it does:** When a Jira release/fix-version is marked as released, an automation collects all issues tagged with that version, groups them by type (Bug, Feature, Improvement), formats a summary, and publishes it as a new Confluence page under a "Release Notes" space.

**Data needed:**
- Jira fix version/release field
- Issue type, summary, description, resolution
- Linked pull requests or commit references (if available via integration)
- Confluence space/page template to publish into

## 3. Cross-Project Dependency Tracker

**Problem it solves:** When multiple teams work on interdependent Jira projects, managers lack visibility into cross-team blockers until a deadline is missed. There's no single view showing which teams are waiting on which other teams.

**What it does:** A scheduled automation that scans for issues with "blocks"/"is blocked by" links across different projects, builds a dependency map, and publishes/updates a Confluence dashboard page showing current cross-team blockers, their owners, and due dates.

**Data needed:**
- Jira issue links (block/blocked-by relationships) across projects
- Project/team ownership metadata (e.g., component or project lead fields)
- Due dates and status for each linked issue
- Confluence page to host the dependency dashboard (updated via API)
