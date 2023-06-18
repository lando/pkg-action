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
