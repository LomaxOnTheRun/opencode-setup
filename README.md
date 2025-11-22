# OpenCode setup

This repo is a playground for setting up OpenCode to run within a repo.

It might also document systemwide OpenCode setup.

## AGENTS.md file

There is a global config file at `~/.config/opencode/AGENTS.md`.

There is a local config file in the repo root, in `AGENTS.md`.

## Adding Prompts to Default Agents

You can customize the behavior of default agents (Build, Plan) by adding custom prompts.

### Steps

1. Create a `prompts/` directory in your repo root
2. Add a prompt file (e.g., `prompts/build.txt`) with your custom instructions
3. Update `opencode.json` to reference the prompt:

```json
{
  "agent": {
    "build": {
      "prompt": "{file:./prompts/build.txt}"
    }
  }
}
```
