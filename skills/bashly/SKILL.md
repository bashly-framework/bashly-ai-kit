---
name: bashly
description: |
   Build, explain, troubleshoot, and maintain Bash command-line applications
   with the Bashly generator. Use for Bashly questions and examples, designing
   command trees, defining flags and arguments in `bashly.yml`, converting shell
   scripts to Bashly, generating command scripts, writing source partials, or
   working on an existing Bashly project.
---

# Bashly Skill

Use this skill for Bashly guidance and for producing or updating Bashly CLIs.

## Choose the Interaction Mode

- For questions, explanations, examples, reviews, or troubleshooting requests,
  answer at the requested depth without changing files or running commands unless
  the user also asks for implementation or validation.
- For implementation requests, inspect the project and carry the change through
  generation and validation when the environment permits it.
- If the user provides a repository or files, tailor the answer or implementation
  to its existing structure and settings.
- State material assumptions. Ask a focused question only when an unresolved
  choice would substantially change the result; otherwise make a reasonable
  assumption and continue.
- Keep explanations practical. Use runnable `yaml` and `bash` examples and show
  expected output when it materially helps.

## Follow Workflow

1. Confirm project mode.
   - Detect whether the user has an existing Bashly project or needs a new one.
   - For existing projects, inspect current Bashly settings and source folder layout before editing.
   - Use `references/bashly-workflow.md` to locate the effective `bashly.yml` when defaults are overridden.
   - When users need non-default paths, add or update settings with `bashly add settings`.

2. Define the CLI contract before editing files.
   - Capture command groups, subcommands, required args, optional args, and flags.
   - Confirm naming and UX details (short flags, long flags, help text, defaults, required constraints).

3. Author or update `bashly.yml`.
   - For new projects, initialize with `bashly init` or `bashly init --minimal` based on requested scope.
   - Keep edits focused and follow the existing project's conventions.
   - Keep descriptions concise and user-facing.
   - Keep command trees predictable and avoid unnecessary nesting.

4. Implement command behavior in Bashly partials.
   - Resolve the active source folder first (default `src`, or overridden in settings/env).
   - Create or update command and shared partial files in that source folder.
   - Keep business logic in partials so regeneration remains safe and repeatable.

5. Generate CLI files with Bashly.
   - Run the Bashly generation command from the project root.
   - If generation is unavailable in the environment, still produce valid `bashly.yml` and list the exact generation command for the user.

6. Validate behavior.
   - Check shell syntax for generated scripts when possible.
   - Exercise representative command paths (`--help`, one success path, one argument/flag error path).

7. Document what changed.
   - Summarize command tree changes and any backward-incompatible flag/argument changes.
   - Summarize which partial files were added/updated in the source folder.
   - Provide quick usage examples for the most important commands.

## Use Bundled Resources

- Read `references/bashly-workflow.md` for command design heuristics, common Bashly operations, and troubleshooting.
- Use the icon asset in `assets/` for skill metadata/UI integration when relevant.

## Use Bashly Reference Sources

- For exact configuration keys, use `bashly doc [SEARCH]` when Bashly is
  installed and read-only command execution is consistent with the interaction
  mode. Use `bashly doc --index` to discover available keys. This reference
  matches the installed Bashly version.
- Do not run `bashly doc` when the user or environment disallows commands;
  recommend the command instead and continue with the available sources.
- When internet access is available, verify syntax and options against official
  Bashly documentation before finalizing changes.
- Prefer Markdown endpoints when retrieving pages from `bashly.dev`: use
  `https://bashly.dev/index.md` for the home page, or remove a page's trailing
  slash and append `.md` (for example,
  `https://bashly.dev/usage/getting-started.md`). Fall back to the normal HTML
  page if a Markdown endpoint is unavailable.
- Prioritize sources in this order: the installed-version reference from
  `bashly doc` when applicable, Bashly docs (`bashly.dev`), the Bashly
  documentation source (`bashly-framework/bashly-book`), official examples,
  then the `bashly-framework/bashly` repository.
- Use current sources especially for settings behavior, advanced features
  (`bashly add ...`), and version-sensitive commands.
- Link users to the normal human-facing documentation page unless the raw
  Markdown is specifically useful. Link to the exact page, section, or source
  location when the user benefits from a citation. Do not invent links.
- If internet access is unavailable, continue using the installed reference,
  local project files, and `references/bashly-workflow.md`, then state which
  sources could not be checked.

## Output Expectations

- Produce only files needed for the requested CLI behavior.
- Ensure required source partials are present so generated scripts implement the requested behavior.
- Keep generated UX consistent: clear descriptions, stable command names, and practical defaults.
- Prefer explicit examples in final responses (`tool command --flag value`) for each major command.
- For troubleshooting, identify the observed failure separately from assumptions and proposed fixes.
