# Bashly Skill for Coding Agents

`bashly` helps an agent build and maintain Bash CLI projects using
[Bashly](https://bashly.dev/).

## What it does

- Builds or updates `bashly.yml` command trees
- Writes and updates Bashly partials in the active source folder (for example under `src/`)
- Uses `bashly init` / `bashly init --minimal` for new projects
- Uses `bashly generate` flows for regeneration
- Handles default and overridden settings layouts (`src`, settings files, env)
- Translates a rough CLI idea into a complete implementation: command design, config, partials, generation, and validation
- Refreshes syntax against official docs/examples when internet is available

## Install in Codex

Use the built-in installer skill:

1. In Codex chat, run `$skill-installer`
2. Ask it to install from this GitHub URL:
   - `https://github.com/bashly-framework/bashly-ai-kit/tree/main/skills/bashly`
3. Restart Codex after install

Alternative prompt:

```
Install this skill from GitHub:
https://github.com/bashly-framework/bashly-ai-kit/tree/main/skills/bashly
```

## Install in Claude Code

Claude Code supports project and user skill locations:

- Project skill: `.claude/skills/bashly/SKILL.md`
- User skill: `~/.claude/skills/bashly/SKILL.md`

Copy `skills/bashly` from this repo into one of those locations
([reference](https://docs.claude.com/en/docs/claude-code/sub-agents#manage-skills)).

## Official references used by the skill

- https://bashly.dev/
- https://bashly.dev/usage/settings/
- https://bashly.dev/examples/
- https://github.com/bashly-framework/bashly
- https://github.com/bashly-framework/bashly/tree/master/examples
