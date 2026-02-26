---
layout: default
title: Installation
order: 2
---

# Installation

## Option A — Use the template (recommended)

The fastest way to get started:

1. Go to [primer2-template](https://github.com/bagustris/primer2-template) and click **Use this template → Create a new repository**
2. In your new repo, go to **Settings → Pages** and set Source to **GitHub Actions**
3. Edit `_config.yml` with your site title and description
4. Push a change — your site deploys automatically

## Option B — Add to an existing site

Add to your site's `_config.yml`:

```yml
remote_theme: bagustris/primer2-theme
plugins:
  - jekyll-remote-theme
  - jekyll-seo-tag
```

Add to your `Gemfile`:

```ruby
gem "github-pages", group: :jekyll_plugins
gem "jekyll-remote-theme"
```

Then run:

```sh
bundle install
bundle exec jekyll serve
```

## Requirements

- Jekyll 3.5–4.x
- Ruby 2.4+
- Works with GitHub Pages out of the box (no custom build step needed)

