# setup-qemu

Proxy for [docker/setup-qemu-action](https://github.com/docker/setup-qemu-action), pinned to a commit SHA. Installs QEMU static binaries so Docker can build and run images for other platforms.

All inputs and outputs are forwarded unchanged, except for pinned defaults; see the upstream documentation for details.

The `image` input defaults to a pinned `tonistiigi/binfmt` tag and digest instead of `latest`.

## Usage

```yaml
- uses: techcode-io/github-actions/setup-qemu@setup-qemu/v1
```
