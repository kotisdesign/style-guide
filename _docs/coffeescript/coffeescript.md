---
layout: page
title: CoffeeScript
permalink: /docs/coffeescript/
---

# CoffeeScript

CoffeeScript is our preferred scripting language for the Rails conversion.  You
should make an attempt use CoffeeScript, though some vendor-specific code may be
difficult and confusing to integrate and Javascript may be easier and more readable.
If you're using Javascript, please leave a brief block-comment note at the top of
the file with the reason for using JS.  This will allow us to go back at a later
time and understand why a decision was made.

## Style

* Use `camelCase` with a leading lowercase for variables, methods, and object
  properties.
* Use `CamelCase` with a leading uppercase for classes.
* Use `SCREAMING_SNAKE_CASE` for constants.
* Denote "private" methods and variables with a leading underscore.
* Prefer lines under 80 characters. Keep all lines under 100.
* Do not use trailing semicolons.
* Do not leave trailing whitespace.

## Functions

* When declaring functions, use a single space after the closing parentheses
  of the argument list.
* {% highlight ruby %}
    my_method = (arg1, arg2) -> # good
    my_method = (arg1, arg2)-> # bad
  {% endhighlight %}

* When chaining method calls and the code doesn't fit on one line, EVERY call
  should be on a separate line and indented one level:
* {% highlight coffeescript %}
    [1..3]
      .map((x) -> x * x)
      .concat([10..12])
      .filter((x) -> x < 11)
  {% endhighlight %}

* Choose to omit or include parentheses when calling functions in a way that
  optimizes readability.

## Other

* Favor `unless` over `if` for negative conditions.
* Do not use `else` with `unless`.  Rewrite to `if..else`.
* Prefer string interpolation over concatenation.
