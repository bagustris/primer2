---
layout: default
title: Layouts
order: 5
---

# Layouts

The theme ships four layouts. All are available to any page in your site via the `layout` front matter key.

## `default`

The main two-column layout. Use this for all regular content pages.

```yaml
---
layout: default
title: My Page
---
```

Renders:
- Fixed left sidebar with the site title, search box, and auto-generated navigation
- Main content area on the right with Primer `markdown-body` styles applied
- Mobile header with hamburger toggle at narrow viewports

This is the layout you will use for almost every page.

## `home`

A thin wrapper around `default`. Identical output — it simply renders `{{ content }}` inside the `default` layout. Provided for semantic clarity when you want your root `index.md` to declare itself as the home page.

```yaml
---
layout: home
---
```

> **Tip:** Using `layout: default` on `index.md` works just as well. `home` is purely a naming convention.

## `page`

Another thin wrapper around `default`. Semantically distinguishes a generic static page (About, Contact, etc.) from a post or the home page.

```yaml
---
layout: page
title: About
---
```

Output is identical to `default`.

## `post`

Wraps `default`. Intended for dated blog posts. No extra rendering logic is added by the theme beyond the `default` layout, but using `layout: post` follows Jekyll convention and makes it straightforward to add post-specific styling later.

```yaml
---
layout: post
title: "My First Post"
date: 2025-01-01
---
```

> **Note:** The sidebar navigation includes all pages that have a `layout` set (unless `nav_exclude: true` is present). Blog posts with `layout: post` will therefore appear in the sidebar by default. Add `nav_exclude: true` to any post you want to keep out of the nav.

## Overriding a layout

Copy the layout file from the theme into your site's `_layouts/` directory and edit it freely. Jekyll will prefer your local copy over the theme's.

```sh
# Example: override the default layout
cp $(bundle show jekyll-theme-primer)/_layouts/default.html _layouts/default.html
```

For smaller additions (favicon, custom fonts, analytics) prefer the `_includes/head-custom.html` hook instead of overriding the full layout. See [Customization](./customization.html) for details.
