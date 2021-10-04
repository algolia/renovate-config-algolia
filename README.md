# renovate-config-algolia

This repository holds a [Renovate shareable configuration](https://renovateapp.com/docs/configuration-reference/config-presets), much like [algolia/eslint-config-algolia](https://github.com/algolia/eslint-config-algolia/).

[Renovate](https://renovateapp.com/) keeps npm dependencies up-to-date the right way, the right features and right time.

## How to use it

### 1. Create a `renovate.json` file:

If you have a **JavaScript application** (dashboard, static website generator), put this in your `renovate.json`:

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

The only difference between the two configurations is that an application will have its `devDependencies` _and_ `dependencies` pinned.
While a JavaScript library will only have its `devDependencies` pinned.
Read the [Renovate docs, dependency pinning](https://renovatebot.com/docs/dependency-pinning/) to learn more.

You do not need to install `renovate-config-algolia`, as it's automatically picked up by Renovate.

### 2. Activate Renovate

Go to <https://github.com/apps/renovate>, ask a GitHub admin of the organisation if you need help on how to do this step.

## What's inside the configuration?

The Renovate configuration automerges any minor and patch updates to any dependencies in your repository.
It will directly push to the GitHub default branch of your project.

It runs every weekend, Paris time.

We chose to have a configuration that directly pushes to GitHub to avoid any notification noise inside GitHub by having a lot of Pull Requests to merge manually.
If the update passes your test suite, then it's merged directly.
If tests are not passing or if there's a major upgrade then a pull request will be opened.
