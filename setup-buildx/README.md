# setup-buildx

Proxy for [docker/setup-buildx-action](https://github.com/docker/setup-buildx-action), pinned to a commit SHA. Sets up Docker Buildx.

All inputs and outputs are forwarded unchanged, except for pinned defaults; see the upstream documentation for details.

The `version` input defaults to a pinned buildx release instead of `latest`.

## Usage

```yaml
- uses: techcode-io/github-actions/setup-buildx@setup-buildx/v1
```
