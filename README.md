# renovate-config-algolia

[Renovate](https://renovateapp.com/) keeps npm dependencies up-to-date. The right
way, the right features.

This repository holds a [shareable configuration](https://renovateapp.com/docs/configuration-reference/config-presets), much like [algolia/eslint-config-algolia](https://github.com/algolia/eslint-config-algolia/).

## How to use it

1. Install it:

```sh
npm install renovate-config-algolia --dev
```

2. Modify your package.json.

If you have a **JavaScript application** (dashboard, static website generator), update your package.json:

```json
{
  "renovate": {
    "extends": ["config:application", "algolia"]
  }
}
```

If you have a **JavaScript library**:

```json
{
  "renovate": {
    "extends": ["config:js-lib", "algolia"]
  }
}
```

The only difference between the two is that, an application, will have `devDependencies` AND `dependencies` pinned. While a JavaScript library will only have `devDependencies` pinned.

[Read more](https://renovateapp.com/docs/deep-dives/dependency-pinning) about dependencies pinning.

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