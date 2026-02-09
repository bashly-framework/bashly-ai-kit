# Bashly AI Kit

This repository includes Bashly resources for AI-assisted workflows, including
coding skills and a Custom GPT companion.

## Custom GPT

For quick learning and ad-hoc help, use the Bashly Custom GPT at
[bashly.dev/chat](https://bashly.dev/chat) (redirects to a ChatGPT custom chat).

This is a good fit if you want Bashly guidance without committing to a Codex or
Claude skill setup.

## Skill for Agents

This skill helps an agent build and maintain Bash CLI projects using
[Bashly](https://bashly.dev/).

### What it does

- Builds or updates `bashly.yml` command trees
- Writes and updates Bashly partials in the active source folder (for example under `src/`)
- Uses `bashly init` / `bashly init --minimal` for new projects
- Uses `bashly generate` flows for regeneration
- Handles default and overridden settings layouts (`src`, settings files, env)
- Translates a rough CLI idea into a complete implementation: command design, config, partials, generation, and validation
- Refreshes syntax against official docs/examples when internet is available

### Install in Codex

Use the built-in installer skill:

In Codex chat, use this prompt

```
install the skill from https://github.com/bashly-framework/bashly-ai-kit/tree/main/skills/bashly
(master branch)
```

### Install in Claude Code

Claude Code supports project and user skill locations:

- Project skill: `.claude/skills/bashly/SKILL.md`
- User skill: `~/.claude/skills/bashly/SKILL.md`

Copy `skills/bashly` from this repo into one of those locations
([reference](https://docs.claude.com/en/docs/claude-code/sub-agents#manage-skills)).
