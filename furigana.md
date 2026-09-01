---
layout: default
title: Furigana
order: 7
---
Furigana are small reading aids printed above kanji to show their
pronunciation. This theme supports them three ways, simplest first.

## Plain markdown

Write `{base|reading}` right in your text, escaping the `|` as `\|`, no
include or raw HTML needed:

```
{漢字\|かんじ} is the Japanese word for "kanji".
```

renders as:

{漢字\|かんじ} is the Japanese word for "kanji".

Give one reading per character to align them precisely, e.g. for compound
words where each kanji has its own reading:

```
{漢字\|かん\|じ}
```

renders as {漢字\|かん\|じ}.

This works because [`assets/js/furigana.js`](https://github.com/bagustris/primer2-theme/blob/master/assets/js/furigana.js)
walks the rendered page after load and swaps `{base|reading}` text for
`<ruby>`/`<rt>` elements — kramdown has no native syntax for this, so it
would otherwise just pass the braces through as literal text. The same
technique (and this exact syntax/regex) is used by
[obsidian-markdown-furigana](https://github.com/steven-kraft/obsidian-markdown-furigana);
it's also how this theme already handles GitHub-style `> [!NOTE]` alert
blockquotes, in `markdown-alerts.js`.

> [!WARNING]
> The `\|` escape is required. kramdown's GFM table syntax treats *any*
> line containing a bare `|` as a one-row table — even mid-sentence — and
> splits it into `<td>` cells before your furigana braces are ever seen.
> Escaping avoids that; kramdown strips the backslash, so the browser still
> sees a plain `|` and `furigana.js` converts it normally. A `|` inside
> inline code (`` `like this` ``) or a fenced code block doesn't need
> escaping — those aren't parsed as table syntax.

> [!NOTE]
> Because the conversion happens in the browser, `{base|reading}` stays as
> literal text in RSS/Atom feeds and anywhere else the page's JS doesn't
> run. Use the include or raw HTML below if you need furigana without JS.

## Shorthand include

The theme also ships a [`furigana.html`](https://github.com/bagustris/primer2-theme/blob/master/_includes/furigana.html)
include. Write a whole sentence in one call and mark each reading as
`[kanji|reading]`:

{% raw %}
```liquid
{% include furigana.html text="[今日|きょう]は[日本語|にほんご]の[勉強|べんきょう]をします。" %}
```
{% endraw %}

renders as:

{% include furigana.html text="[今日|きょう]は[日本語|にほんご]の[勉強|べんきょう]をします。" %}

Text outside the brackets is passed through untouched, so you only mark the
words that need a reading. For a single word, `reading=` also works:

{% raw %}
```liquid
{% include furigana.html text="漢字" reading="かんじ" %}
```
{% endraw %}

renders as {% include furigana.html text="漢字" reading="かんじ" %}. Unlike
the plain-markdown syntax above, this renders server-side, so it works even
without JS.

## Raw HTML

Kramdown passes raw HTML straight through, so the standard `<ruby>` element
always works too, with no include or JS:

```html
<ruby>漢字<rt>かんじ</rt></ruby>
```

<ruby>漢字<rt>かんじ</rt></ruby> is the Japanese word for "kanji".

> [!NOTE]
> Unlike a custom Liquid tag, an `_includes/*.html` file ships with the theme
> and works through `remote_theme` — the same mechanism this site already
> relies on for `sidebar-nav.html`. A custom plugin would not: this site's
> `Gemfile` pulls in the `github-pages` gem, which forces Jekyll's
> `safe: true`, and safe mode never loads a site's `_plugins/` directory
> (nor any gem plugin outside GitHub's approved list) — even when building
> through GitHub Actions rather than GitHub's own infrastructure.
