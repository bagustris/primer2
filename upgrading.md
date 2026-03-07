---
layout: default
title: Upgrading
order: 10
---

# Upgrading

## Check your current version

If you pin to a tag in `_config.yml`, the version is explicit:

```yml
remote_theme: bagustris/primer2-theme@v0.6.0
```

If you use the unversioned form, you are always on the latest commit of the default branch:

```yml
remote_theme: bagustris/primer2-theme
```

Check the [releases page](https://github.com/bagustris/primer2-theme/releases) for the latest version and its changelog.

## Upgrading to a newer version

### Pinned version

Update the tag in your `_config.yml`:

```yml
# before
remote_theme: bagustris/primer2-theme@v0.6.0

# after
remote_theme: bagustris/primer2-theme@v0.7.0
```

Commit the change and push — GitHub Pages will rebuild with the new version.

### Unpinned (latest)

No action needed in `_config.yml`. Trigger a rebuild by pushing any change (e.g., a whitespace edit). GitHub Pages refetches the remote theme on every build.

To force a rebuild without a code change, re-run the Pages workflow from the **Actions** tab of your repository.

## After upgrading

### Test locally

```sh
bundle update
bundle exec jekyll serve
```

Check the site visually and run the CI suite if you have one:

```sh
script/cibuild
```

### Review the changelog

Read the release notes for the version you upgraded to. Pay attention to:

- **Breaking changes** — layout or include file renames, removed front matter keys
- **New front matter keys** — optional features you may want to enable
- **CSS class changes** — relevant if you override `_includes/head-custom.html` or `assets/css/style.scss`

## Overridden files

If you have copied any theme files into your own site (layouts, includes, sass), those local copies take priority over the theme and **will not receive theme updates automatically**. After upgrading:

1. Compare your local copy against the updated theme source.
2. Merge any relevant upstream changes by hand.

You can inspect the theme source in your bundle:

```sh
bundle show jekyll-theme-primer
# prints the path, e.g. /home/user/.bundle/ruby/3.2.0/gems/jekyll-theme-primer-0.7.0
```

## Downgrading

Pin to any previous tag:

```yml
remote_theme: bagustris/primer2-theme@v0.5.0
```
