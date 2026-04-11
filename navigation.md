---
layout: default
title: Navigation
order: 9
---

# Sidebar Navigation

The sidebar navigation is generated automatically from your site's pages at build time. No manual menu configuration is needed.

## How it works

The `_includes/sidebar-nav.html` include collects every page that:

1. Has a `layout` value set in its front matter, **and**
2. Does **not** have `nav_exclude: true`, **and**
3. Produces HTML output (pages whose URL ends in `.xml`, `.txt`, `.scss`, `.css`, or `.json` are skipped)

The third rule keeps plugin- and theme-generated files such as `feed.xml` (jekyll-feed), `sitemap.xml` (jekyll-sitemap), `robots.txt`, and `assets/css/style.scss` out of the sidebar even when they inherit a `layout` value from a site-wide `_config.yml` default.

It then sorts the remaining pages: those with an `order` value come first (ascending), followed by pages without `order` sorted alphabetically by title.

{% raw %}
```liquid
{% assign ordered   = nav_pages | where_exp: "p", "p.order != nil" | sort: "order" %}
{% assign unordered = nav_pages | where_exp: "p", "p.order == nil" | sort: "title" %}
```
{% endraw %}

## Controlling order

Add an `order` integer to any page's front matter. Lower numbers appear higher in the list.

```yaml
---
layout: default
title: Getting Started
order: 1
---
```

Pages without `order` are appended after all ordered pages, sorted alphabetically.

### Recommended ordering

| Page | Suggested `order` |
|---|---|
| Introduction / index | 1 |
| Installation | 2 |
| Configuration | 3 |
| Core feature pages | 4–20 |
| Reference / API | 50–79 |
| Contributing | 99 |

## Excluding pages from the nav

Set `nav_exclude: true` on any page you do not want to appear in the sidebar:

```yaml
---
layout: default
title: Search
permalink: /search/
nav_exclude: true
---
```

Common candidates for exclusion: the dedicated `/search/` page, draft pages, and dated blog posts.

## Active link highlighting

The current page's link receives the CSS class `active`, styled with a left border accent. This is handled automatically by comparing `nav_page.url` to `page.url` inside `sidebar-nav.html`.

## Page title in the nav

The label shown in the sidebar uses:

1. `page.title` from front matter if present
2. Otherwise, the filename with hyphens and underscores replaced by spaces and the first letter capitalised

```yaml
---
layout: default
title: Quick Start   # ← this is shown in the sidebar
---
```

## Customising the nav include

Copy `_includes/sidebar-nav.html` from the theme into your own `_includes/` directory. Jekyll will use your local copy at build time, giving you full control over the markup and Liquid logic.

```sh
cp $(bundle show jekyll-theme-primer)/_includes/sidebar-nav.html _includes/sidebar-nav.html
```
