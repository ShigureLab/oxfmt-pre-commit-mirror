# oxfmt-pre-commit-mirror

Mirror of the `oxfmt` pre-commit hook for `pre-commit`, using the [PyPI distribution](https://pypi.org/project/oxfmt/). Supports `pre-commit` versions 2.9.2 and later. No Node.js installation is required.

## Usage

Add this to your `.pre-commit-config.yaml`:

```yaml
- repo: https://github.com/ShigureLab/oxfmt-pre-commit-mirror
  rev: v0.69.0
  hooks:
    - id: oxfmt
```

The hook uses the same JavaScript/JSX/TypeScript/TSX file selection and default options as the [upstream hook](https://github.com/oxc-project/mirrors-oxfmt).

## Package source

The `oxfmt` PyPI package is an unofficial distribution maintained by [oxc-py](https://github.com/dhruvkb/oxc-py), which repackages the [upstream Oxc binaries](https://github.com/oxc-project/oxc). This repository only pins that package; it does not publish packages to PyPI.

Mirror versions track PyPI, not npm, and can lag upstream releases. Installing the hook requires an available platform wheel: macOS x86_64/ARM64, Linux x86_64/ARM64 (glibc 2.18+ or musl 1.2+), or Windows x86_64. There is no source-build fallback.

## Automation

Like the other ShigureLab hook mirrors, `mirror.py` checks PyPI daily, updates the pinned dependency and README, and creates version commits and tags. The Mirror workflow requires the `PRE_COMMIT_HOOK_AUTO_UPDATE_TOKEN` repository or organization secret with write access to this repository. The Release workflow publishes GitHub releases from `v*` tags.
