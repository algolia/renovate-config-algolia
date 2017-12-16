# renovate-config-algolia

This repository holds a [shareable configuration](https://renovateapp.com/docs/configuration-reference/config-presets), much like [algolia/eslint-config-algolia](https://github.com/algolia/eslint-config-algolia/).

[Renovate](https://renovateapp.com/) keeps npm dependencies up-to-date. The right
way, the right features and right time.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [How to use it](#how-to-use-it)
  - [1. Install the configuration:](#1-install-the-configuration)
  - [2. Modify your package.json.](#2-modify-your-packagejson)
  - [3. Activate renovate](#3-activate-renovate)
- [What's inside the configuration?](#whats-inside-the-configuration)
- [Requirements](#requirements)
- [Releasing](#releasing)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## How to use it

### 1. Install the configuration:

```sh
npm install renovate-config-algolia --dev
```

### 2. Create a renovate.json file:

If you have a **JavaScript application** (dashboard, static website generator), put in `renovate.json`:

```json
{
  "extends": ["config:js-app", "algolia"]
}
```

If you have a **JavaScript library**:

```json
{
  "extends": ["config:js-lib", "algolia"]
}
```

The only difference between the two configuration is that, an application, will have `devDependencies` AND `dependencies` pinned. While a JavaScript library will only have `devDependencies` pinned.

[Read more](https://renovateapp.com/docs/deep-dives/dependency-pinning) about dependencies pinning.

### 3. Activate renovate

Go to https://github.com/apps/renovate, ask a GitHub admin of the organisation if you need help on how to do this step.

## What's inside the configuration?

This configuration is made to automerge any minor and patch updates to any dependencies in your repository. It will directly push to the GitHub default branch of your project.

It runs every weekend, Paris time.

We choosed to have a configuration that directly push to GitHub to avoid any notification noise inside GitHub by having a lot of Pull Requests to merge manually. If the update passes your test suite, then it's merged directly. If tests are not passing or if there's a major upgrade then a pull request will be opened.

## Requirements

You can't use protected branch features along with this configuration. This is currently a [limitation from GitHub](https://platform.github.community/t/repositories-which-have-protected-branches-with-push-restrictions-have-no-ability-to-grant-push-rights-to-integrations/1376/36).

If protected branches are activated on your repository, disable them (settings).

## Releasing

```sh
# change package.json
git commmit -am 'feat(renovate): more goodness'
npm run release
```
