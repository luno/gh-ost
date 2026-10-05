# Luno release process

This fork ships its own artifacts, named `luno-gh-ost` so they cannot be confused with upstream `gh-ost`.

## Tags

Tags are `v<upstream-version>-luno.<N>`, for example `v1.1.8-luno.1`. Pushing a `v*` tag triggers `.github/workflows/release.yml`. The version embedded in the binary is the tag without its leading `v`.

## What the workflow produces

Built via `Dockerfile.packaging` and `build.sh`, then verified (checksums, embedded version), attested for provenance and published as a GitHub release:

- `luno-gh-ost-<os>-<arch>.tar.gz` for linux and darwin on amd64 and arm64, each containing a `luno-gh-ost` binary
- `luno-gh-ost.<arch>.rpm` and `luno-gh-ost.<arch>.deb` (package name `luno-gh-ost`) for linux
- `SHA256SUMS`

## Consuming a release

Luno's core repo pins a release tag plus the SHA256 of `luno-gh-ost-linux-amd64.tar.gz` (taken from `SHA256SUMS`). Bump both together when taking a new release.
