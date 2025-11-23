# OpenCode setup

This repo is a playground for setting up OpenCode to run within a repo.

It might also document systemwide OpenCode setup.

## AGENTS.md file

There is a global config file at `~/.config/opencode/AGENTS.md`.

There is a local config file in the repo root, in `AGENTS.md`.

## Tools vs permissions

Tools can be switched on or off (`true` or `false`). If a tool is switched off, agents will not be able to access it at all and permissions for it will be ignored.

Permissions apply to tools which are switched on for an agent, and specify how freely a tool can be used (`allow`, `ask`, or `deny`).

## Subagents

There is currently no way to restrict use of a specific subagent to certain primary agents (e.g. allow the Build agent to use a subagent but not allow the Plan agent to use that same subagent).

Primary agents can have access to _all_ or _none_ of the subagents:

```
{
  $schema: https://opencode.ai/config.json,
  agent: {
    build: {
      mode: primary,
      tools: {
        task: true  // Can use ALL subagents
      }
    },
    plan: {
      mode: primary,
      tools: {
        task: false  // Cannot use ANY subagents
      }
    }
  }
}
```

For now the way to restrict agents is to create different primary agents and manually switch between them (e.g. create a Git primary agent as the only one able to run dangerous git commands).

Allowing safe bash commands requires duplicating the permissions across all agents. I can probably also use global permissions in the `opencode.json` file to allow some globally safe commands.
