---
layout: default
title: Troubleshooting
order: 11
---

# Troubleshooting

## Site doesn't build on GitHub Pages

**Symptom:** The GitHub Actions workflow fails or the Pages URL shows a 404.

**Checks:**

1. Confirm `remote_theme: bagustris/primer2-theme` is set in `_config.yml`.
2. Confirm `jekyll-remote-theme` is listed under `plugins:` in `_config.yml`.
3. Confirm the Pages source is set to **GitHub Actions** (Settings → Pages → Source).
4. Check the Actions log for the specific error line.

## Sidebar navigation shows no pages

**Symptom:** The sidebar is empty or only shows the search box.

**Cause:** Pages must have a `layout` set in their front matter. Pages without `layout` are excluded from the auto-generated nav.

**Fix:** Add `layout: default` to every content page:

```yaml
---
layout: default
title: My Page
---
```

## Pages appear in wrong order in the sidebar

The sidebar sorts by `order` (ascending), then alphabetically. If ordering looks wrong, check:

- All pages you want ordered have an integer `order` value (not a string).
- No two pages share the same `order` value (ties are resolved arbitrarily).

## Search returns no results

**Symptom:** Typing in the search box produces no matches.

**Cause:** The search index file `/assets/search.json` is missing from your repository.

**Fix:** Copy the file from [primer2-template](https://github.com/bagustris/primer2-template/blob/master/assets/search.json) into your site's `assets/` directory. Commit and push.

## MathJax / Mermaid not rendering

These features are **opt-in per page**. You must add the corresponding front matter key:

```yaml
---
mathjax: true   # enable MathJax on this page
mermaid: true   # enable Mermaid on this page
---
```

If you have added the key but rendering still fails, check the browser console for network errors loading the CDN scripts.

## Custom CSS is not applied

**Symptom:** Styles added to `assets/css/style.scss` have no effect.

**Check:** Your `style.scss` must begin with a YAML front matter block (two `---` lines) for Jekyll to process it:

```scss
---
---

@import "{{ site.theme }}";

/* your custom styles here */
```

Also ensure Sass variable overrides appear **before** the `@import` line, not after.

## Sidebar width override not working

CSS specificity may cause your rule to be overridden. Use more specific selectors or `!important` as a last resort:

```css
.book-sidebar  { width: 300px !important; min-width: 300px !important; }
.book-content  { margin-left: 300px !important; }
```

## Mobile hamburger menu does not open

**Symptom:** Tapping the ☰ button on mobile has no effect.

**Cause:** A JavaScript error elsewhere on the page can prevent the sidebar toggle script from running.

**Fix:** Open the browser console, identify and resolve any JS errors, then reload.

## `site.github.*` variables are empty locally

These variables are populated by `jekyll-github-metadata`, which reads from the GitHub API. They are empty during local development unless you export a `JEKYLL_GITHUB_TOKEN` environment variable with a personal access token.

For local development you can safely ignore this; the variables are populated correctly on GitHub Pages.

## RuboCop failures in CI

Run RuboCop locally to see the offences:

```sh
bundle exec rubocop -D --config .rubocop.yml
```

Auto-correct safe offences with:

```sh
bundle exec rubocop -a --config .rubocop.yml
```

## Getting more help

- **Theme bugs** → [primer2-theme issues](https://github.com/bagustris/primer2-theme/issues)
- **Docs issues** → [primer2 issues](https://github.com/bagustris/primer2/issues)
