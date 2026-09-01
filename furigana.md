---
layout: default
title: Furigana
order: 7
---
Furigana are small reading aids printed above kanji to show their
pronunciation. This theme supports them two ways.

## Shorthand include

The theme ships a [`furigana.html`](https://github.com/bagustris/primer2-theme/blob/master/_includes/furigana.html)
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

renders as {% include furigana.html text="漢字" reading="かんじ" %}.

## Raw HTML

Kramdown passes raw HTML straight through, so the standard `<ruby>` element
always works too, with no include:

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
