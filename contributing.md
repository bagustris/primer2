---
layout: default
title: Contributing
order: 99
---

# Contributing

Contributions to `primer2-theme` are welcome!

## Development setup

```sh
git clone https://github.com/bagustris/primer2-theme
cd primer2-theme
script/bootstrap    # install Ruby dependencies
script/server       # preview demo at localhost:4000
```

## Running tests

```sh
script/cibuild
```

This runs a Jekyll build, HTML validation (htmlproofer + W3C), and RuboCop.

## Submitting changes

1. Fork [primer2-theme](https://github.com/bagustris/primer2-theme)
2. Create a branch: `git checkout -b my-fix`
3. Make your change and verify tests pass: `script/cibuild`
4. Open a pull request — one fix or feature per PR

## Reporting issues

- **Theme bugs** → [primer2-theme issues](https://github.com/bagustris/primer2-theme/issues)
- **Docs issues** → [primer2 issues](https://github.com/bagustris/primer2/issues)

See [CODE_OF_CONDUCT.md](https://github.com/bagustris/primer2-theme/blob/master/LICENSE.md) for community guidelines.
