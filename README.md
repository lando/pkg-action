# Pkg Action

This is a GitHub action that allows you to "compile" node projects with [pkg](https://github.com/vercel/pkg). It supports:

* All `pkg` supported node versions
* `x64|amd64` and `aarch64|arm64`
* `macos|linux|windows`.

If you are also looking to code sign/notarize the resulting binaries then check out [@lando/code-sign-action](https://github.com/marketplace/actions/code-sign-action).

### Caveats

* If you are looking to "cross compile" binaries across OS **AND** architecture then we recommend you matrix strategy across this actions `os` and `arch` inputs instead of `runs-on`. This is neccessary because `arm64` compilation is currently emulated on Linux only. If you are compiling just on `amd64|x64` then it's _probably_ ok to use `runs-on`.
* If you are looking to "cross compile" binaries across OS **AND** architecture **AND** code sign/notarize the resulting binaries we recommend you first upload the artifacts and then download them to the `os` you need to do the code signing.

See [Advanced Usage](#advanced-usage) below for some examples of ^.

## Required Inputs

These keys must be set correctly for the action to work.

| Name | Description | Example Value |
|---|---|---|
| `entrypoint` | The binary entrypoint path.  | `bin/entrypoint.js` |

## Optional Inputs

These keys are set to sane defaults but can be modified as needed.

| Name | Description | Default | Example |
|---|---|---|---|
| `arch` | The architecture to build for. | `amd64` | `x64` \| `amd64` \| `aarch64` \| `arm64` |
| `config` | The config file to use. | `package.json` | `config.json` |
| `node-version` | The node version to package with. | `node14` | `node8` \| `node10` \| `node12` \| `node14` \| `node16` \| `latest` |
| `options` | Additional options and flags to pass into pkg. | `null` | Additional [pkg options](https://github.com/vercel/pkg#usage) |
| `os` | The operating system to build for. | `${{ runner.os }}` | `linux` \| `macos` \| `win` |
| `pkg` | The version on @vercel/pkg to use. | `5.8.0` | `latest` |
| `upload` | Upload the artifacts. Useful if you need to grab them for downstream for things like code signing. | `true` | `false` \| `true` |

## Outputs

```yaml
outputs:
  file:
    description: "The path to the generated binary."
    value: ${{ steps.pkg-action.outputs.file }}
  artifact-key:
    description: "The artifact upload key."
    value: ${{ steps.pkg-action.outputs.artifact-key }}
```

##  Usage

### Basic Usage

```yaml
name: Package into node binary
uses: lando/pkg-action@v2
with:
  entrypoint: bin/cli
```

### Advanced Usage

**ALL OPTIONS**
```yaml
name: Package into node binary
uses: lando/pkg-action@v2
with:
  entrypoint: bin/cli
  arch: arm64
  config: package.json
  node-version: node16
  options: -C
  os: win
  upload: false
```

**CROSS COMPILE ON ALL THE THINGS**
```yaml
runs-on: ubuntu-20.04
strategy:
  matrix:
    arch:
      - x64
      - arm64
    node-version:
      - node16
    os:
      - linux
      - macos
      - win
steps:
  - name: Package into node binary
    uses: lando/pkg-action@v2
    with:
      entrypoint: bin/cli
      arch: ${{ matrix.arch }}
      node-version: ${{ matrix.node-version }}
      os: ${{ matrix.os }}
```

## Changelog

We try to log all changes big and small in both [THE CHANGELOG](https://github.com/lando/pkg-action/blob/main/CHANGELOG.md) and the [release notes](https://github.com/lando/pkg-action/releases).

## Releasing

1. Correctly bump versions, tag things and push to github

  ```bash
  yarn release
  ```

2. Publish to [GitHub Actions Marketplace](https://docs.github.com/en/enterprise-cloud@latest/actions/creating-actions/publishing-actions-in-github-marketplace)

## Contributors

<a href="https://github.com/lando/pkg-action/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=lando/pkg-action" />
</a>

Made with [contrib.rocks](https://contrib.rocks).

## Other Resources

* [Important advice](https://www.youtube.com/watch?v=WA4iX5D9Z64)
