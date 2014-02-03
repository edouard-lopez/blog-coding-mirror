---
layout: post
title: "How to Localize content with HandlebarsJS"
date: 2014-01-14 15:52
comments: true
categories: [ HTML5, HandlebarsJS, tip, l10n, i18n, jQuery ]
tags: [ HTML5, HandlebarsJS, tip, l10n, i18n, jQuery ]
published: false
---

When working on the revamp of the [screenshots page for the _Probe Meteo project_](http://probe-meteo.com/screenshots.html#/en), I hit a wall in terms of **internalization support in `Handlebars`**. More precisely, there is no native support, but it is possible to implement it [using `Helpers`](http://handlebarsjs.com#helpers).

[![Localization of Probe Meteo screenshots page](/images/screenshots/handlebar-localization.png)](/images/screenshots/handlebar-localization.png)

This article describe how I implemented a basic localization mechanism using an ` helper`.
<!--more-->

## JSON data

For each _datum_ you want to localize, you have to define its value as an object where each:

* _key_ is an [ISO 639-1 code](https://en.wikipedia.org/wiki/ISO_639-1) (_e.g._ `en` for _English_, `fr` for _French_, etc.) ;
* _value_ is the string translated in the target language.

Below is the `JSON` used to translate a screenshot's _title_ and _description_:

```json
{
    "screenshots": [
    {
        "title": {
            "en": "Wind barb (hairy) Chart without Tooltip",
            "fr": "Histogramme vectoriel"
        },
        "long-desc": {
            "en": "Show the direction and strength of the wind…",
            "fr": "Indique la direction et la force du vent…"
        }
    }
}
```

## Template

{% raw %}
```html
<div class="caption">
    <h3 class="title">{{localize title}}</h3>
    <p>{{localize long-desc}}</p>
</div>
```
{% endraw %}

## Handlebars Helper

```js
$(function(){
    'use strict';

    Handlebars.registerHelper('localize', function(msg) {
        var regex = /.*([\w]{2})/;
        var l10n = location.hash.match(regex)[1];

        return msg[l10n] || msg['en'];
    });
});
```
