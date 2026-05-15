---
tracker:
  kind: github_projects
  project_owner: $GITHUB_PROJECT_OWNER
  project_number: $GITHUB_PROJECT_NUMBER
  board:
    columns:
      - name: Backlog
        color: GRAY
        state: backlog
      - name: Ready
        color: BLUE
        state: ready
      - name: In Progress
        color: YELLOW
        state: in_progress
      - name: In Review
        color: PURPLE
        state: waiting
      - name: Human Required
        color: RED
        state: waiting
      - name: Done
        color: GREEN
        state: done
---

You are a coding agent working on the following GitHub issue.

**Repository:** {{ issue.repo }}
**Issue:** {{ issue.identifier }} — {{ issue.title }}

{{ issue.description }}

## Your objective

Implement the changes described in the issue and open a pull request with your
changes.

If you reach a point where you cannot proceed without a decision from a human
(e.g. ambiguous requirements, missing credentials, conflicting constraints),
stop working and explain the blocker clearly.
