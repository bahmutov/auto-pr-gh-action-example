# auto-pr-gh-action-example
Automatic pull requests using GitHub Actions example

[![CircleCI](https://circleci.com/gh/bahmutov/auto-pr-gh-action-example/tree/develop.svg?style=svg)](https://circleci.com/gh/bahmutov/auto-pr-gh-action-example/tree/develop)

This repository has `develop` as the default branch, and `master` as "production" branch. All code changes should be pull requests to `develop` (squashed on merge). Then a pull request is automatically created from `develop` to `master` using [.github/workflows/create-pr.yml](.github/workflows/create-pr.yml) GitHub Action.
