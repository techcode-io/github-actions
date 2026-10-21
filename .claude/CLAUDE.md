# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Monorepo of reusable GitHub Actions. Each top-level directory (e.g. `setup-github-bot/`) is one independently versioned action with its own `action.yml` and `README.md`. There is no build, lint or local test tooling: everything is validated by GitHub Actions workflows.

## Testing

- Each action has `.github/workflows/test-<action>.yml`, triggered on `workflow_call` and on pull requests / pushes to `main` that touch `<action>/**` or the test workflow itself.
- Tests run the action from the local path (`uses: ./<action>`) and then assert its effects in a shell step. They run on a matrix of ubuntu, macos and windows, so use `shell: bash` and portable commands.

## Release architecture

`.github/workflows/release.yml` (manual `workflow_dispatch`, inputs `action` and `version` as `X.Y.Z`):

1. `validate` (inline Python): checks the action name and version format and that `<action>/action.y(a)ml` exists. It also uses `git ls-remote` to make sure the tag doesn't exist yet, because the shallow checkout has no tags. It outputs `tag=<action>/vX.Y.Z` and `major=<action>/vX`.
2. `test-<action>`: one job per action calling its test workflow. `uses:` cannot be dynamic, so each job is gated by `if: inputs.action == '<action>'`.
3. `publish`: pushes the immutable tag, force-moves the floating major tag and creates a GitHub release (`--latest=false`, because releases are per action).

`publish` must list every `test-<action>` job in `needs` and in its `if` condition. An action without a test job cannot be released.

Consumers reference actions by prefixed tag: `techcode-io/github-actions/<action>@<action>/v1`.

## Adding an action

1. Create `<action>/action.yml` and `<action>/README.md`.
2. Add `.github/workflows/test-<action>.yml` (copy an existing one).
3. In `release.yml`, add a `test-<action>` job and its clause to `publish` (`needs` and `if`).
4. Add the action to the table in the root `README.md`.

## Conventions

- Commit messages follow Conventional Commits (`feat:`, `fix:`, `chore:`, ...).
- YAML files start with `---`.
