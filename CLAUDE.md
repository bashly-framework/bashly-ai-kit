# AGENTS.md

## Repository Purpose

This repository is **Bashly AI Kit**. It is a support repo for AI-assisted Bashly workflows, not a single end-user CLI project.

It contains:
- A reusable **Bashly skill** for coding agents (`skills/bashly/`)
- Prompt assets for chat/agent contexts (`prompts/`)
- Documentation describing how these pieces are used (`README.md`)

## What This Repo Is For

Use this repo when you need to:
- Improve the Bashly coding skill instructions
- Update references/examples used by the skill
- Maintain agent prompt files for Bashly-focused assistants
- Keep installation/use docs accurate

## Key Paths

- `README.md`: top-level project overview and installation notes
- `skills/bashly/SKILL.md`: canonical Bashly skill instructions
- `skills/bashly/references/bashly-workflow.md`: detailed workflow/reference guide
- `skills/bashly/agents/openai.yaml`: agent metadata for OpenAI-style integrations
- `skills/bashly/agents/claude.yaml`: agent metadata for Claude Code integrations (note: Claude Code uses `SKILL.md` frontmatter directly; this file mirrors `openai.yaml` for parity)
- `skills/bashly/assets/`: icons used by agent metadata
- `prompts/prompt.md`: long-form prompt for the Bashly assistant persona
- `prompts/AGENTS.md`: portable agent instruction file template/example

## Working Rules For AI Agents

1. Treat this as a **docs/instructions repo** first.
2. Prefer minimal, targeted edits; preserve existing structure and tone.
3. Keep `README.md`, `skills/bashly/SKILL.md`, and references in sync when behavior changes.
4. Do not invent Bashly behavior; align with official Bashly docs when making technical claims.
5. When updating prompts or skills, optimize for actionable, testable workflows (clear steps, commands, expected outcomes).

## Typical Change Types

- Refine Bashly workflow instructions
- Add or clarify troubleshooting steps
- Update installation guidance
- Improve prompt quality and guardrails
- Adjust agent metadata (display text/icons/default prompt)

## Definition Of Done

A change is complete when:
- Relevant docs are updated consistently across affected files
- Instructions remain internally coherent (no conflicting steps)
- Examples/commands are plausible for Bashly users
- The repository still reads as a kit for enabling Bashly-capable AI agents
