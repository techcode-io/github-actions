<h1 align="center">GitHub Actions</h1>

<p align="center">
  <i align="center">Mono repository of reusable GitHub Actions used across techcode.io workflows.</i>
</p>

<h4 align="center">
  <a href="https://github.com/techcode-io/github-actions/actions/workflows/test-setup-github-bot.yml">
    <img src="https://img.shields.io/github/actions/workflow/status/techcode-io/github-actions/test-setup-github-bot.yml?branch=main&label=ci&style=flat-square" alt="continuous integration" style="height: 20px;">
  </a>
  <a href="https://github.com/techcode-io/github-actions/graphs/contributors">
    <img src="https://img.shields.io/github/contributors-anon/techcode-io/github-actions?color=yellow&style=flat-square" alt="contributors" style="height: 20px;">
  </a>
  <a href="https://opensource.org/licenses/Apache-2.0">
    <img src="https://img.shields.io/badge/apache%202.0-blue.svg?style=flat-square&label=license" alt="license" style="height: 20px;">
  </a>
  <br>
</h4>

- [Source](https://github.com/techcode-io/github-actions)
- [Documentation](https://github.com/techcode-io/github-actions)
- [Issues](https://github.com/techcode-io/github-actions/issues)
- [Contact](mailto:adrien.mannocci@gmail.com)

## :package: Prerequisites

- A GitHub repository using GitHub Actions workflows.

## :sparkles: Features

- One directory per action, versioned and released independently.
- Each action is tested by its own workflow, only when it changes.
- Per-action tags: an immutable `<action>/vX.Y.Z` and a floating `<action>/vX`.

## :dart: Motivation

- We needed a single place to share the actions used across our repositories.
- Each action should be testable and releasable on its own, without versioning the whole repository.

## :hammer: Workflow

### Setup

The following steps will ensure your project is cloned properly.

1. Clone repository:
   ```shell
   git clone https://github.com/techcode-io/github-actions
   cd github-actions
   ```

### Test

- Each action has a dedicated workflow named `.github/workflows/test-<action>.yml`.
- It runs on pull requests and pushes to `main` when files under `<action>/**` change.

### Add an action

1. Create `<action>/action.yml` and `<action>/README.md`.
2. Add `.github/workflows/test-<action>.yml` (copy an existing one). It must trigger on `workflow_call` and on changes under `<action>/**`.
3. Add a `test-<action>` job and its clause in the `publish` condition of `.github/workflows/release.yml`.
4. Add the action to the table below.

### Release

- Run the **Release action** workflow with the action directory and a `X.Y.Z` version.
- It runs the action's test workflow, then pushes the tag `<action>/vX.Y.Z`, moves the floating `<action>/vX` tag and creates a GitHub release.

## 📖 Usage

Each action is referenced by its prefixed tag:

```yaml
- uses: techcode-io/github-actions/<action>@<action>/v1
```

| Action                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| [setup-buildx](setup-buildx)          | Proxy for `docker/setup-buildx-action`           |
| [setup-github-bot](setup-github-bot)  | Configure git to commit as `github-actions[bot]` |
| [setup-qemu](setup-qemu)              | Proxy for `docker/setup-qemu-action`             |
| [setup-uv](setup-uv)                  | Proxy for `astral-sh/setup-uv`                   |

## :heart: Contributing

If you find this project useful here's how you can help, please click the :eye: **Watch** button to avoid missing
notifications about new versions, and give it a :star2: **GitHub Star**!

You can also contribute by:

- Sending a [Pull Request](https://github.com/techcode-io/github-actions/pulls) with your awesome new features and bug fixed.
- Be part of the community and help resolve [Issues](https://github.com/techcode-io/github-actions/issues).

## 🧾 License

The `github-actions` project is free and open-source software licensed under the Apache-2.0 license.
