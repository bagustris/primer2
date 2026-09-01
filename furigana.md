---
layout: default
title: Furigana
order: 7
---
Furigana are small reading aids printed above kanji to show their
pronunciation. This theme supports them two ways.

## Raw HTML

Kramdown passes raw HTML straight through, so the standard `<ruby>` element
always works, no plugin required:

```html
<ruby>漢字<rt>かんじ</rt></ruby>
```

<ruby>漢字<rt>かんじ</rt></ruby> is the Japanese word for "kanji".

## Shorthand include

Typing `<ruby>`/`<rt>` for every word gets tedious in a full sentence, so the
theme ships an [`furigana.html`](https://github.com/bagustris/primer2-theme/blob/master/_includes/furigana.html)
include:

{% raw %}
```liquid
{% include furigana.html text="漢字" reading="かんじ" %}
```
{% endraw %}

Call it once per word to build up a sentence:

{% raw %}
```liquid
{% include furigana.html text="今日" reading="きょう" %}は{% include furigana.html text="日本語" reading="にほんご" %}の{% include furigana.html text="勉強" reading="べんきょう" %}をします。
```
{% endraw %}

renders as:

{% include furigana.html text="今日" reading="きょう" %}は{% include furigana.html text="日本語" reading="にほんご" %}の{% include furigana.html text="勉強" reading="べんきょう" %}をします。

> [!NOTE]
> Unlike a custom Liquid tag, an `_includes/*.html` file ships with the theme
> and works through `remote_theme` — the same mechanism this site already
> relies on for `sidebar-nav.html`. A custom plugin would not: this site's
> `Gemfile` pulls in the `github-pages` gem, which forces Jekyll's
> `safe: true`, and safe mode never loads a site's `_plugins/` directory
> (nor any gem plugin outside GitHub's approved list) — even when building
> through GitHub Actions rather than GitHub's own infrastructure.
