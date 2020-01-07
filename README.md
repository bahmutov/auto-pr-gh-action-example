# auto-pr-gh-action-example [![Mergify Status][mergify-status]][mergify] [![CircleCI](https://circleci.com/gh/bahmutov/auto-pr-gh-action-example/tree/develop.svg?style=svg)](https://circleci.com/gh/bahmutov/auto-pr-gh-action-example/tree/develop)
> Automatic pull requests using GitHub Actions example

This repository has `develop` as the default branch, and `master` as "production" branch. All code changes should be pull requests to `develop` (squashed on merge). Then a pull request is automatically created from `develop` to `master` using [.github/workflows/create-pr.yml](.github/workflows/create-pr.yml) GitHub Action.

**Note:** workflow actions [cannot trigger other workflows](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/events-that-trigger-workflows#about-workflow-events) and [this issue](https://github.com/pascalgn/automerge-action#limitations). If one workflow creates a pull request, other workflows cannot merge it automatically.

To get around workflow to workflow problem, only the `create-pr` GH action is used in this repo. Every time you land a pull request into `develop` this action opens a PR into `master` with label `auto-pr`. Then [Mergify](https://mergify.io) bot notices the pull request, waits for CircleCI to successfully build it, and merges the PR, see settings in [.mergify.yml](.mergify.yml) file.

I have left the [.github/workflows/merge-pr.yml](.github/workflows/merge-pr.yml) just for show. If you open a pull request from `develop` to `master` manually, add label `auto-pr`, then this action will merge it automatically, see [.mergepal.yml](.mergepal.yml) settings.

[mergify]: https://mergify.io
[mergify-status]: https://img.shields.io/endpoint.svg?url=https://gh.mergify.io/badges/bahmutov/auto-pr-gh-action-example&style=flat
