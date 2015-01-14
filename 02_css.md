---
layout: page
title: CSS
permalink: /css/
---

# CSS

When starting a new application, please install the [PureCSS framework](http://purecss.io/)
into the vendor-specific assets folder.

You must also install the responsive grids bundle, which is *not* included
with the standard `pure.css` file!

## File Organization

SCSS and CSS files should be organized in the following fashion:

{% highlight text %}
assets/stylesheets
├── base
│   ├── global-styles.scss
│   ├── mixins.scss
│   └── variables.scss
├── styles
│   ├── admin
│   │   ├── estores.scss
│   │   └── other-css.scss
│   ├── carts.scss
│   ├── categories.scss
│   ├── estores.scss
│   └── carts.scss
├── application.css
├── main.css
└── other-sprockets-directives.css
{% endhighlight %}

* Base styles should include variables, mixins, and global styles used throughout
  the application.
* The styles directory should group stylesheets into logical bundles.
* Vendor plugins should go into the `/vendor/assets/` directory and required
  using Sprockets.
* Use Sprockets to require files for precompilation and use with the Rails asset
  pipeline.  However, you should use a file with `@import` directives to control
  which files are included and in which order:
* {:.codeblock} {% highlight css %}
    /* using the example above */
    /* application.css */

    /*
     *= require jquery.ui.all
     *= require font-awesome
     *= require main
     *= require_self
     */
  {% endhighlight %}
* {:.codeblock} {% highlight css %}
    /* main.css */
    @import "base/variables";
    @import "base/mixins";
    @import "base/global-styles";

    @import "styles/carts";
    @import url(//fonts.googleapis.com/etc);
  {% endhighlight %}

* The only files in the `assets/stylesheets` directory should be Sprockets
  manifest files and css files with import directives.
* Always precompile assets and reference stylesheets in rails through Sprockets
  manifests and the asset pipeline.

## Class and ID Naming

* Use meaningful or generic id/class names instead of presentational names.  Names
  should describe the *purpose*  of the element in question.
* {:.codeblock} {% highlight css %}
    /* good */
    #header {}
    #footer {}
    .video {}

    /* bad */
    .small-font {}
    .float-left {}
    .clear {}
    #kotisid-12345 {}
    #uniq9282 {}
  {% endhighlight %}

* Elements that occur **exactly once** should use IDs, otherwise, use classes.
* When naming classes and IDs, split words using hyphens, not underscores.
* When styling a component, prefer an element + class namespace over element + id.
  Use as little specificity as possible.
* {:.codeblock} {% highlight html %}
    <ul class="category-list">
      <li class="item">Category 1</li>
      <li class="item">
        <a href="category2.html">Category 2</a>
      </li>
    </ul>
  {% endhighlight %}

* {:.codeblock} {% highlight css %}
    .category-list { /* element + class namespace */

      /* this selects only direct descendants */
      > li {
        list-style-type: none;
      }

      /* minimum specificity */
      a {
        color: #e6b;
      }
    }
  {% endhighlight %}

* If you're using an ID selector, ensure you do not use more than one in your
  rule declaration:
* {:.codeblock} {% highlight css %}
    /* this is too specific */
    #header .search-bar #search-results {}
  {% endhighlight %}

* Classes named `disabled`, `danger`, `hover`, `selected`, `active` should
  always be namespaced by an element.
* {:.codeblock} {% highlight css %}
    /* good */
    option.selected {}
    button.danger {}

    /* bad */
    .selected {}
    .danger {}
  {% endhighlight %}

## Coding Style

### Spacing
* Use soft tabs with a two-space indent.
* Always remove trailing whitespace.
* Always put a space after `:` in property declarations.
* Always put spaces before `{` in rule declarations.
* Always end property declarations with a semi-colon.
* Always end rule declarations with a `}` on a new line.
* Put line breaks between rule sets.
* Rules and properties should be on their own lines.

### Formatting
* Use hex codes for color `#000` unless using `rgba()`.
  * Prefer shorthand hex codes when possible: `#000` over `#000000`.
* Do not specify units for `0` values: `margin: 0;` over `margin: 0px;`.
* Prefer single-quotation marks over double.
* Prefer `/* */` comment blocks instead of `//`.
* <strike>Organize property declarations alphabetically, when possible. Ignore vendor
  prefixes for alphabetization purposes.</strike>

### SCSS-Specific
* Try to limit nesting to three levels.  If you need to go more, you should
  reconsider the specificity or the layout.
* Nested rules should come AFTER the properties from the parent rule.

* {:.codeblock} {% highlight css %}
    // Example of good basic formatting practices
    .styleguide-format {
      background-color: rgba(0, 0, 0, .5);
      border: 1px solid #0f0;
      color: #000;
      .nested-item {
        color: #f00;
      }
    }

    // Example of individual selectors getting their own lines
    .multiple,
    .classes,
    .get-new-lines {
      display: block;
    }
{% endhighlight %}

## Miscellaneous

* We're still working on the pixels vs ems.
* Avoid the use of style hacks.  They're usually not needed.
* Be consistent.  When editing existing code, try to match the
  existing style--after all, we want it to be consistent for readability's sake.
