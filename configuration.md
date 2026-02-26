---
layout: default
title: Configuration
order: 3
---

# Configuration

All configuration goes in your site's `_config.yml`.

## Required

```yml
remote_theme: bagustris/primer2-theme
plugins:
  - jekyll-remote-theme
  - jekyll-seo-tag
```

## Recommended

```yml
title: My Site
description: A short description of your site

exclude:
  - README.md
  - Gemfile
  - vendor/
```

## Optional

```yml
google_analytics: UA-XXXXXXXX-X   # Google Analytics tracking ID
```

## Page front matter

Each `.md` content page supports:

| Variable | Type | Description |
|---|---|---|
| `layout` | string | Use `default` for all content pages |
| `title` | string | Page title shown in the sidebar nav |
| `order` | integer | Controls position in sidebar (lower = higher) |
| `nav_exclude` | boolean | Set `true` to hide from sidebar nav |
| `permalink` | string | Override the URL, e.g. `/about/` |

### Example

```yaml
---
layout: default
title: Getting Started
order: 2
---
```

### Hide a page from nav

```yaml
---
layout: default
title: Hidden
nav_exclude: true
---
```

## Search

Search is built-in and requires no configuration. It reads from `/assets/search.json` at build time. Make sure that file exists in your repo (it is included in `primer2-template`).
