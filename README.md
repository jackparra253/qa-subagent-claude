# qa-subagent-claude

A Claude Code [subagent](https://docs.claude.com/en/docs/claude-code/sub-agents) that acts as a meticulous QA engineer — test planning, bug hunting, edge-case analysis, and implementation verification.

This is a Claude Code port of GitHub's [`qa-subagent.agent.md`](https://github.com/github/awesome-copilot/blob/main/agents/qa-subagent.agent.md) custom Copilot agent (from the [awesome-copilot](https://github.com/github/awesome-copilot) catalog), adapted to Claude Code's subagent format.

## What's included

- **`.claude/agents/qa.md`** — the `qa` subagent definition: a QA persona with a 5-step workflow (scope → test plan → write/execute tests → exploratory testing → report), test quality standards, a bug report format, and anti-patterns to avoid.
- **`.claude/commands/qa.md`** — a `/qa` slash command that delegates to the subagent.

## Installation

Copy both files into your own project (for project-level availability) or into `~/.claude/` (to make the agent available across all your projects):

```
.claude/agents/qa.md
.claude/commands/qa.md
```

No extra configuration is needed — the agent has no `tools` restriction, so it inherits full tool access from Claude Code.

## Usage

- Explicitly: `/qa review this feature for edge cases`
- Or ask Claude directly: "use the qa agent to verify this change"
- Claude Code may also invoke it proactively after implementing or changing a feature, per the agent's `description`.

## Why port it

GitHub Copilot's custom chat agents and Claude Code's subagents share the same shape: YAML frontmatter (`name`, `description`, optionally `tools`/`model`) plus a Markdown body used as the system prompt. Porting an agent between the two mostly means dropping the frontmatter fields that don't translate (Copilot's `tools: vscode, execute, read, agent, edit, search, web, todo` has no clean 1:1 mapping) and keeping the persona/workflow body as-is.

## License

The persona, workflow, and bug report format are adapted from the original `qa-subagent.agent.md` in [github/awesome-copilot](https://github.com/github/awesome-copilot).
