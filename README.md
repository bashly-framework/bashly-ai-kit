# Bashly AI Kit

Bashly AI Kit provides reusable instructions and references for working with
[Bashly](https://bashly.dev/) in Codex, Claude Code, and other coding-agent
environments.

The repository contains:

- A reusable Bashly skill under `skills/bashly/`
- A portable `AGENTS.md` template under `templates/`

The skill helps coding agents:

- Learning Bashly concepts and configuration
- Building or updating `bashly.yml` command trees
- Writing Bashly command and library partials
- Locating projects that use non-default settings or source paths
- Generating and validating Bashly CLIs when the host can run commands
- Troubleshooting errors with current Bashly documentation and examples

Capabilities depend on the host. A coding agent can edit a repository, run
Bashly, and validate the generated CLI when those tools are available.

## Install the Skill

### Codex

Use the built-in skill installer with this request:

```text
Install the skill from https://github.com/bashly-framework/bashly-ai-kit/tree/master/skills/bashly
```

### Claude Code

Ask Claude Code to install the skill in your user skills directory:

```text
Install the Bashly skill from https://github.com/bashly-framework/bashly-ai-kit
into my user skills directory (~/.claude/skills/bashly/)
```

For manual installation or project-level installation, see the
[Claude Code skills reference](https://code.claude.com/docs/en/skills).

## Update the Skill

Ask your coding agent to replace the existing installation with the current
version from GitHub:

```text
Update the installed Bashly skill from:
https://github.com/bashly-framework/bashly-ai-kit/tree/master/skills/bashly

Replace the existing installation.
```

## Zero-install AGENTS.md Template

If installing a skill is not practical, copy
[`templates/AGENTS.md`](templates/AGENTS.md) into the root of a Bashly project.
It gives a coding agent a compact Bashly workflow without requiring a global
installation.

For example, place it in a new empty directory and ask your agent:

```text
Build a Bashly CLI with subcommands for several categories of funny,
motivational quotes, and print one random quote for the selected category.
```

The skill is the canonical maintained workflow. Keep the template aligned with
the skill where the two formats overlap.
