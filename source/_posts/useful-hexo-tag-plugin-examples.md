---
title: Useful Hexo Tag Plugin Examples
date: 2020-03-01 22:38:37
categories: Example
tags: [hexo, hexo-next, tag-plugin]
---

* [Tag Plugins | Hexo](https://hexo.io/docs/tag-plugins)

```js _.compact http://underscorejs.org/#compact Underscore.js
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
```

{% include_code lang:javascript hello.js %}

{% gist b4ca9da82784588756c697bf7bacc388 %}

`<!-- more -->`

<!-- more -->

{% youtube BoJ0pfhMmfU %}

* [Tag Plugins | NexT](https://theme-next.org/docs/tag-plugins/)

{% tabs Sixth unique name %}

<!-- tab Buttons @window-close -->
{% btn #, Text & Large Icon & Title, home fa-fw fa-lg, Title %}
<!-- endtab -->

<!-- tab Labels @code -->
{% label default@default %}
{% label primary@primary %}
{% label success@success %}
{% label info@info %}
{% label warning@warning %}
{% label danger@danger %}
<!-- endtab -->

<!-- tab Notes @exclamation-circle -->
{% note default %}
#### Header
default note
{% endnote %}

{% note primary %}
#### Header
primary note
{% endnote %}

{% note success %}
#### Header
success note
{% endnote %}

{% note info %}
#### Header
info note
{% endnote %}

{% note warning %}
#### Header
warning note
{% endnote %}

{% note danger %}
#### Header
danger note
{% endnote %}
<!-- endtab -->

{% endtabs %}
