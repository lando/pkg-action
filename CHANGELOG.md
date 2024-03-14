## v5.0.0 - [March 14, 2023](https://github.com/lando/pkg-action/releases/tag/v5.0.0)

### **BREAKING CHANGES**

* Added support for `node20`
* Changed default `node` version to `node20`
* Changed default `arch` to `${{ runner.arch }}`
* Improved `arch` behavior so emulation is only used if needed
* Updated default `pkg` package to `@yao-pkg/pkg@5.11.5` since `vercel/pkg` is **DEPRECATED**

## v4.0.0 - [December 4, 2023](https://github.com/lando/pkg-action/releases/tag/v4.0.0)

### **BREAKING CHANGES**

* `pkg` input now takes any valid spec eg `@yao-pkg/pkg@5.10.0` as opposed to just the `versions`

## v3.0.1 - [September 28, 2023](https://github.com/lando/pkg-action/releases/tag/v3.0.1)

* Reverted `node-sync` do to extreme slowness using `node16` in `arm64` environment

## v3.0.0 - [September 28, 2023](https://github.com/lando/pkg-action/releases/tag/v3.0.0)

### New Features

* Bumped default `pkg` input to `pkg@5.8.0`
* Bumped default `node-version` input to `16`
* Disabled `--debug` by default. Added support for debug toggling via https://github.blog/changelog/2022-05-24-github-actions-re-run-jobs-with-debug-logging
* Synced `node-version` usage so it is used in all relevant build environments

### **BREAKING CHANGES**

* `node-version` input is now just a major version eg `16` instead of `node16`

## v2.2.2 - [June 17, 2023](https://github.com/lando/pkg-action/releases/tag/v2.2.2)

* Switched release flow over to [@lando/prepare-release-action](https://github.com/lando/prepare-release-action)

## v2.2.1 - [April 27, 2023](https://github.com/lando/pkg-action/releases/tag/v2.2.1)

* Switched `set-output` and `save-state` to new `$GITHUB_OUTPUT` and `$GITHUB_STATE`. See [this](https://github.blog/changelog/2022-10-11-github-actions-deprecating-save-state-and-set-output-commands/)
* Updated core actions to `v3`

## v2.2.0 - [March 1, 2023](https://github.com/lando/pkg-action/releases/tag/v2.2.0)

* Added input `pkg` to specify version of [@vercel/pkg](https://github.com/vercel/pkg)
* Fixed bug where installed `pkg` version was not consistent across `arch`

## v2.1.0 - [March 1, 2023](https://github.com/lando/pkg-action/releases/tag/v2.1.0)

* Bumped to `node@16`
* Bumped to `pkg@5.8.0`
* Improved feedback on `pkg` version installed

## v2.0.1 - [April 13, 2022](https://github.com/lando/pkg-action/releases/tag/v2.0.1)

* Added `icon` and `color` branding

## v2.0.0 - [April 12, 2022](https://github.com/lando/pkg-action/releases/tag/v2.0.0)

* First release
