# cursor-env

A workspace environment for the [Cursor IDE](https://www.cursor.com/), pre-configured with common development tools, editor settings, and AI behaviour guidelines.

## What's included

| Path | Purpose |
|------|---------|
| `.github/workflows/copilot-setup-steps.yml` | Pre-installs tools in the [GitHub Copilot cloud agent](https://docs.github.com/en/copilot/how-tos/agents/copilot-coding-agent) environment |
| `.devcontainer/devcontainer.json` | Dev container definition — open the repo in Cursor (or VS Code) and it will spin up a fully-configured Ubuntu container |
| `.cursor/rules/general.mdc` | Workspace-level AI rules applied to every Cursor chat and inline edit |

## Getting started

### Open in a dev container (recommended)

1. Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) (already included when you open the repo in Cursor).
2. Open the repository in Cursor.
3. When prompted, click **Reopen in Container** (or run `Dev Containers: Reopen in Container` from the command palette).

The container image is based on Ubuntu 22.04 and includes:

- **Node.js 20** + TypeScript, Prettier, ESLint
- **Python 3.12** + Ruff, Black, Mypy
- **GitHub CLI**, Git, ripgrep, fd, jq, and other common CLI tools

### Copilot cloud agent

The `.github/workflows/copilot-setup-steps.yml` workflow pre-installs the same toolset in the ephemeral environment used by the [GitHub Copilot coding agent](https://docs.github.com/en/copilot/how-tos/agents/copilot-coding-agent), so the agent can build, lint, and test code without extra setup time.

### Cursor AI rules

Rules in `.cursor/rules/` are picked up automatically by Cursor and applied to AI interactions in this workspace. Edit `general.mdc` (or add new `.mdc` files) to adjust the coding conventions that the AI follows.

## Customisation

- **Add languages**: extend the `features` block in `.devcontainer/devcontainer.json` with any [Dev Container Feature](https://containers.dev/features) you need.
- **Add tools to the agent**: add `run` steps to `.github/workflows/copilot-setup-steps.yml`.
- **Change AI behaviour**: edit or add rule files under `.cursor/rules/`.
