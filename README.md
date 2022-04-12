# Pkg Action

This is a GitHub action that allows you to "compile" node projects with [pkg](https://github.com/vercel/pkg). It supports:

* All `pkg` supported node versions
* `x64|amd64` and `aarch64|arm64`
* `macos|linux|windows`.

If you are also looking to code sign/notarize the resulting binaries then check out

* CODE SIGN ACTION
* NOTARIZE ACTION

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
| `os` | The operating system to build for. | `${{ runner.os }}` | `win` |
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

### Advanced Usage


## Changelog

We try to log all changes big and small in both [THE CHANGELOG](https://github.com/lando/pkg-action/blob/main/CHANGELOG.md) and the [release notes](https://github.com/lando/pkg-action/releases).

## Releasing

```bash
yarn release
```

## Contributors

<a href="https://github.com/lando/pkg-action/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=lando/pkg-action" />
</a>

Made with [contrib.rocks](https://contrib.rocks).

## Other Resources

* [Important advice](https://www.youtube.com/watch?v=WA4iX5D9Z64)
