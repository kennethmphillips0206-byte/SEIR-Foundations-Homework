# Lesson 3 — Jira Incident Management

- **Date:** 2026-11-13 (America/Chicago)
- **Jira plan:** Free
- **Space:** Balerica AI Incident Management (team-managed)
- **Space key:** BAI (changed from the default KAN)

## Work items

| Key | Type | Summary | Notes |
|---|---|---|---|
| BAI-1 | Task | TEST - EC2 application error | Manual test incident from the install lab |
| BAI-2 | Epic | Balerica AI incident tracking | Groups all Balerica AI incident work |
| BAI-3 | Story | Investigate EC2 application errors | Child of BAI-2, estimated at 3 story points |

## Evidence

| Screenshot | What it shows |
|---|---|
| [jira_estimation_on.jpg](screenshots/jira_estimation_on.jpg) | Space settings → Features with Estimation turned on |
| [jira_epic.jpg](screenshots/jira_epic.jpg) | Epic BAI-2 opened, with its description |
| [jira_story.jpg](screenshots/jira_story.jpg) | Story BAI-3 with parent BAI-2 and a story point estimate of 3 |
| [jira_task.jpg](screenshots/jira_task.jpg) | Task BAI-1 opened, with its summary and description |
| [jira_backlog.jpg](screenshots/jira_backlog.jpg) | Backlog view showing BAI-1 on the board and BAI-3 in the backlog (3 points total) |

## Notes

- The Backlog wasn't on the Features page in my version of Jira. I added it from the **+** at the end of the space tabs.
- Epics don't show up as rows in the Backlog. BAI-3 shows its Epic as a tag instead.
- No API token was created. That comes in the jira.py lab.
