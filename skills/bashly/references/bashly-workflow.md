# Bashly Workflow Reference

## Table of Contents

1. Quick sequence
2. Common commands
3. Locate active project configuration
4. Look up Bashly documentation
5. Design heuristics
6. Troubleshooting checklist

## 1) Quick sequence

1. Create or open a project root.
2. Locate active Bashly settings and source folder.
3. Define CLI contract (commands, args, flags, help text).
4. Edit the active `bashly.yml`.
5. Create or update Bashly partials in the active source folder.
6. Generate scripts with Bashly.
7. Run `--help` and representative commands.

## 2) Common commands

Run these from the project root as applicable:

- `bashly init`
- `bashly init --minimal`
- `bashly add settings`
- `bashly doc [SEARCH]`
- `bashly doc --index`
- `bashly generate`
- `bashly generate --upgrade`

If Bashly is not installed, state that clearly and continue by producing a complete `bashly.yml` plus the exact commands required to generate the final script once Bashly is installed.

## 3) Locate active project configuration

By default, Bashly source files (including `bashly.yml`) are under `./src`.
Users can override defaults through settings. Inspect in this order:

1. Check whether `BASHLY_SETTINGS_PATH` is set in the environment.
2. Check for `./bashly-settings.yml` in the project root.
3. Check for `./settings.yml` in the project root.
4. If no override applies, use default `./src`.

Key settings to inspect in the active settings file:

- `source_dir`: root for Bashly source files (defaults to `src`).
- `config_path`: path for the main Bashly config (`bashly.yml` by default).

For settings details and fields, consult: `https://bashly.dev/usage/settings/`.

Settings can also be provided via environment variables (for example `BASHLY_SOURCE_DIR`, `BASHLY_CONFIG_PATH`). Check environment overrides when file-based settings do not match observed behavior.

Practical inspection commands:

- `echo "${BASHLY_SETTINGS_PATH:-<unset>}"`
- `ls -la`
- `ls -la src`

After identifying the active settings source, inspect its configured paths first, then inspect the resolved `bashly.yml` before making edits.

When implementing command behavior, add or update partial files in the resolved source folder rather than editing generated output directly.

## Official references

- Main docs: `https://bashly.dev/`
- Getting started: `https://bashly.dev/usage/getting-started/`
- Command cheatsheet: `https://bashly.dev/cheatsheet/`
- Settings docs: `https://bashly.dev/usage/settings/`
- Configuration docs: `https://bashly.dev/configuration/`
- Advanced topics index: `https://bashly.dev/advanced/`
- Source repository: `https://github.com/bashly-framework/bashly`
- Examples: `https://github.com/bashly-framework/bashly/tree/master/examples`
- Rendered examples docs: `https://bashly.dev/examples/`

High-value examples to consult first:

- `minimal`, `commands`, `commands-nested` for baseline structure.
- `split-config` for multi-file configuration layout.
- `settings` for source/config path overrides.
- `reusable-flags`, `conflicts`, `needs` for flag UX patterns.
- `filters`, `validations`, `hooks` for advanced command behavior.
- `render-markdown`, `render-mandoc` for docs generation flows.

## 4) Look up Bashly documentation

Use `bashly doc [SEARCH]` for the configuration reference that matches the
installed Bashly version. It supports focused lookups such as:

- `bashly doc command`
- `bashly doc command.flags`
- `bashly doc catch_all`
- `bashly doc flag. --index`

Use `bashly doc --index` to list reference keys. This command is most useful for
configuration fields and their accepted values; use the full documentation for
tutorials, examples, and broader workflows.

When retrieving a page from `bashly.dev`, prefer its Markdown representation:

- Home page: `https://bashly.dev/index.md`
- A page ending in `/`: remove the trailing slash and append `.md`.
- Example: `https://bashly.dev/usage/getting-started/` becomes
  `https://bashly.dev/usage/getting-started.md`.

If the Markdown endpoint is unavailable, use the normal HTML page or the source
in `https://github.com/bashly-framework/bashly-book`. In user-facing answers,
normally link to the HTML page rather than the raw Markdown representation.

### Online refresh checklist

Use this when internet access is available and the task depends on current syntax/features:

1. Check the installed-version reference with `bashly doc [SEARCH]` when command
   execution is allowed and the question concerns configuration syntax.
2. Confirm the operation in official docs, preferably through the matching
   `bashly.dev` Markdown endpoint, before editing project files.
3. Validate structure against one similar official example (`bashly.dev/examples` or repo `examples/`).
4. If behavior seems version-sensitive, check repo state/release notes before concluding.
5. Prefer project-local conventions only when they do not contradict official docs.

## 5) Design heuristics

- Keep top-level commands task-oriented (`build`, `deploy`, `list`) and stable over time.
- Prefer explicit long flags and optional short aliases only when they are obvious.
- Put required arguments first and keep argument names concrete (`environment`, `image_tag`).
- Use command descriptions that tell the user what happens, not implementation details.
- Minimize hidden behavior; expose impactful options as flags.

## 6) Troubleshooting checklist

- Generation fails:
  - Confirm active source path contains `bashly.yml` (not always project root).
  - Confirm Bashly CLI is available in PATH.
- Command missing after generation:
  - Re-check indentation and nesting in `bashly.yml`.
  - Re-run generation and inspect overwritten files.
- Help text looks wrong:
  - Verify each command and flag includes a clear `help` string.
