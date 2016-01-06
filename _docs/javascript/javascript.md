---
layout: page
title: Javascript
permalink: /docs/javascript/
---

# JavaScript

## Style

* Use `camelCase` with a leading lowercase for variables, methods, and object
  properties.
* Use `CamelCase` with a leading uppercase for classes.
* Use `SCREAMING_SNAKE_CASE` for constants.
  * Never use `const` - it's not supported in IE.
* ALWAYS use semi-colons.
* ALWAYS use curly-braces when starting/ending blocks and functions.  Start the
  curly brace on the same line as the block and end on a new line.
* Use whitespace to break code in logical paragraphs.
* Prefer single quotes `'` for strings.

## Functions

* Nested functions are okay.
* Do not declare functions within blocks.
* {% highlight javascript %}
    // bad
    if (x) {
      function foo() {};
    }

    // good
    if (x) {
      var foo = function() {};
    }
  {% endhighlight %}

## Other

* Avoid using `eval()`.  This can be very dangerous and can usually be avoided.
* Do not use a `for..in` loop UNLESS iterating over a hash.  It's best to use
  the standard `for` loop in most cases.
* BE CONSISTENT.
