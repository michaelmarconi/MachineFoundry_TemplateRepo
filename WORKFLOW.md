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

Implement the changes described in the issue. When you are done:

- Open a pull request with your changes.
- Move the issue card to **In Review**.

If at any point you are blocked and need human input, move the card to
**Human Required** and leave a comment explaining what is needed.
