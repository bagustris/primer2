---
layout: default
title: Customization
order: 4
---

# Customization

## Custom CSS

Create `/assets/css/style.scss` in your site:

```scss
---
---

@import "{{ site.theme }}";

/* Your custom styles here */
.book-sidebar {
  width: 300px;
}
```

> **Note:** Sass variable overrides must go *before* the `@import` line.

## Override a layout

Copy [`_layouts/default.html`](https://github.com/bagustris/primer2-theme/blob/master/_layouts/default.html) from the theme into your own `_layouts/default.html` and edit freely.

## Custom head content

Create `/_includes/head-custom.html` in your site to inject anything into `<head>` (favicon, custom fonts, additional CSS):

```html
<link rel="shortcut icon" type="image/x-icon" href="{{ '/favicon.ico' | relative_url }}">
<link rel="preconnect" href="https://fonts.googleapis.com">
```

## Google Analytics

Paste your GA snippet into `/_includes/head-custom-google-analytics.html` in your site.

## Sidebar width

Override in your custom CSS:

```css
.book-sidebar  { width: 280px; min-width: 280px; }
.book-content  { margin-left: 280px; }
```

## Content max-width

```css
.book-content-inner { max-width: 960px; }
```
## Markdown Header

Example of markdown header 

```
---
layout: default
title: Home
order: 1
---
```   
If you want to exclude a page, e.g., `index.md` from the sidebar, add `exclude: true` to the markdown header:

```---
nav_exclude: true
---
```