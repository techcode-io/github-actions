# setup-uv

Proxy for [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv), pinned to a commit SHA. Installs uv and optionally caches its dependencies.

All inputs and outputs are forwarded unchanged, except for pinned defaults; see the upstream documentation for details.

The `version` input defaults to a pinned uv release instead of `latest`; it is ignored when `version-file` is set.

## Usage

```yaml
- uses: techcode-io/github-actions/setup-uv@setup-uv/v1
```
