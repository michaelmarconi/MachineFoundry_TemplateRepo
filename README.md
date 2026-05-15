# My Project

> This repository was created from the [Machine Foundry template](https://github.com/michaelmarconi/MachineFoundry_TemplateRepo).
> It is pre-configured to work with the Machine Foundry orchestrator out of the box.

## What is Machine Foundry?

[Machine Foundry](https://github.com/michaelmarconi/MachineFoundry) is an orchestrator that watches this repository's GitHub Projects
board and automatically dispatches AI coding agents to work on issues that reach
the **Ready** column.

## Board columns

The default board shape ships ready to use:

| Column | State | Meaning |
|---|---|---|
| Backlog | `backlog` | Not yet ready; parked for later |
| Ready | `ready` | Agent will be dispatched automatically |
| In Progress | `in_progress` | Agent is actively working |
| In Review | `waiting` | Agent has finished; awaiting review |
| Human Required | `waiting` | Blocked on human input |
| Done | `done` | Work complete |

When Machine Foundry starts, it shapes the GitHub Projects board to match these
columns automatically.

## Customising the workflow

Edit [`WORKFLOW.md`](./WORKFLOW.md) to:

- **Rename or recolour columns** — change `name` and `color` freely; the `state`
  value controls behaviour, not the name.
- **Add columns** — add entries with any of the five states: `backlog`, `ready`,
  `in_progress`, `waiting`, `done`.
- **Change the agent prompt** — replace the Markdown body below the `---` front
  matter separator with whatever instructions suit your project.

## Connecting to Machine Foundry

Set the following environment variables in your Machine Foundry configuration:

```
GITHUB_TOKEN=<personal access token with project read/write scope>
GITHUB_PROJECT_OWNER=<your GitHub username or org>
GITHUB_PROJECT_NUMBER=<the numeric ID of your GitHub Projects board>
```

The `GITHUB_PROJECT_NUMBER` is the number in the board URL:
`https://github.com/users/<owner>/projects/<number>`

Then start Machine Foundry:

```bash
python -m machinefoundry
```

Machine Foundry will shape the board on first run and begin watching for items in
the **Ready** column.

## Moving issues to Ready

Any issue on the board can be moved to **Ready** manually. Machine Foundry will:

1. Verify the issue has no unresolved blockers or incomplete sub-tasks.
2. Dispatch an AI agent to work on it.
3. Move the card to **In Progress** and record the agent session URL.
4. Move the card to **In Review** when the agent is done.
