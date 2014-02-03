---
layout: post
title: "Bootstrapping Multiple Instances of an HandlebarsJS Template into a Page"
date: 2014-01-12 14:16
comments: true
categories: [ HTML5, HandlebarsJS, tip, jQuery ]
tags: [ HTML5, HandlebarsJS, tip, jQuery ]
published: true
---

This article presents a method to easily re-use an [Handlebars](http://handlebarsjs.com/) template with different JSON data.

To this purpose we will first hook into the _template holder_ using an HTML `class` attributes, then we will bootstrap the data-set linked in the `data-json` attribute.
I'm going to use `jQuery` to get the list of the hooks, inject the given data-set and inflate the template into the page.

## Template Instance(s)

The set-up to bootstrap mulitple instances of the template is pretty straigh-forward, for each instance we will add a block element with a `class="hook"` and a `data-json="path/to.json"` attribute, as shown below:
```html
<div class="hook" data-json="data/set-one.json"></div>
<div class="hook" data-json="data/set-two.json"></div>
…
<div class="hook" data-json="data/set-whatever.json"></div>
```
This describe **where to inflate your template and with what data-set**.

## JavaScript resources

Then you will need to add the **helper**, and your –compiled– **template** (_e.g._ `screenshots.hbs.js`) to your page:
```html
<!-- Helper to inject data-set in templates instance -->
<script src="scripts/template-loader.js"></script>
<!-- Get the (compiled) template -->
<script src="scripts/screenshots.hbs.js"></script>
```

## Template loader

The _template loader_ list the hooks present on the page, [inject the given dataset](http://api.jquery.com/deferred.then/) into the template (currently [hard-coded](#going-further)… _boo, boo!_). Finally we inflate the template at the location of the hook.

```js scripts/template-loader.js
$(function(){
    'use strict';
    var compiledTemplate = myApp.Templates['app/templates/screenshots.hbs'];

    $('.hook').each(function(i, h){              # h = current hook
        var url = $(h).data('json');             # data-set's url
        $.getJSON(url).then(function (json) {    # fetch data-set
            var tpl = compiledTemplate( json );  # inject data into template
            $(h).html(tpl);                      # inflate template in page
        });
    });
});
```

## Template

The template is not really relevant for this mechanism, but in case you want to test with some real sample. However, be aware that this is not a [compiled template](https://github.com/wycats/handlebars.js/#precompiling-templates):
{% raw %}
```html scripts/screenshots.hbs
<ul class="thumbnails row">
    {{#each screenshots}}
    <li class="col-md-{{item-size}}">
        <div class="thumbnail">
            <a href="./{{url.img-full}}" data-lightbox="shots"  title="{{localize title}}">
                <img alt="{{localize title}}" title="{{localize title}}" src="./{{url.img-full}}">
            </a>
            <div class="caption">
                <h3 class="title">{{localize title}}</h3>
                <p>{{localize long-desc}}</p>
            </div>
        </div>
    </li>
    {{/each}}
</ul>
```
{% endraw %}

<a id="going-further" class='hide'></a>
## Going Further

The idea is pretty basic and this article just lay down the foundation. So feel free to hack into the code, for instance you could define the template to use (_cf._ `compiledTemplate`) in the same way as the data-set, _i.e._ with a `data-*` attribute.

## References

* [Manually pre-compile an HandlebarsJS template](https://github.com/wycats/handlebars.js/#precompiling-templates) ;
* [Grunt plugin to Precompile Handlebars templates to JST file](https://npmjs.org/package/grunt-contrib-handlebars) ;
* [Initial approach](https://gist.github.com/edouard-lopez/5655842) and [feedback by David Bruant](https://twitter.com/DavidBruant)
