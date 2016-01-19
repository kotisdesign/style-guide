---
layout: page
title: Ruby
permalink: /docs/ruby/
---

# Ruby

## Background

Much of the Ruby section of this style guide comes from the semi-official
[Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide).  Not all styles
suggested in that guide are applicable, though, and this page should take priority.


Remember to **be consistent** and ensure readable code!

## Style

* Use soft tabs with a two space indent.
* ALWAYS remove trailing white space.
* End your file with an empty line.
* Your editor should be set to use unix-style line endings.
    * In Sublime Text, specify a setting:
    * {% highlight ruby %}
        "default_line_ending": "unix"
      {% endhighlight %}
* Prefer lines under 80 characters. Keep all lines under 100.
    * In Sublime Text, rulers are a good way of keeping track.
      Specify a setting:
    * {% highlight ruby %}
        "rulers": [80, 100]
      {% endhighlight %}

* Do not use block comments.
* {% highlight ruby %}
    # bad
    =begin
    comment line
    another comment line
    =end

    # good
    # comment line
    # another comment line
  {% endhighlight %}

* Use spaces after operators, commas, semicolons, and curly braces.
* {% highlight ruby %}
    2 + 2 = 4
    first, second = 1, 2
    { first: value, second: value }
  {% endhighlight %}

* Do not use spaces after brackets, parentheses, or `!`.
* {% highlight ruby %}
    [1, 2, 3].length
    method(argument).upcase
    !space_after_bang
  {% endhighlight %}

* Avoid single line methods (including empty body methods).
* {% highlight ruby %}
    # good
    def my_good_method
      body
    end

    def my_good_empty_body_method
    end

    # bad
    def bad_method; end
  {% endhighlight %}

* When using `case` statements, indent `when` as deep as `case`.
* {% highlight ruby %}
    case tracking_number
    when begins_with('1Z') then 'UPS'
    when begins_with('5000') then 'USPS'
    else 'Unknown'
    end
  {% endhighlight %}

* When assigning a conditional result to a variable, preserve alignment:
* {% highlight ruby %}
    # good
    shipping_method = if shipping_speed == 'Express'
                        'UPS Next Day Air'
                      else
                        'UPS Ground'
                      end

    # good; especially at conserving line length
    email_message =
      if products_ordered? && in_production?
        'your items should be completed soon'
      else
        'your items will be ready in approximately 2 weeks'
      end
  {% endhighlight %}

* Use empty lines between methods and to split methods into logical paragraphs.
* {% highlight ruby %}
    def first_method
      data = initialize(options)

      data.manipulate!

      data
    end

    def second_method
      result
    end
  {% endhighlight %}

* When continuing a chained method invocation on another line keep the `.` on the second line.
* {% highlight ruby %}
    # good
    one.two.three
      .four

    # bad
    one.two.three.
      four
  {% endhighlight %}

* Align the parameters of a method call if they span more than one line.
* {% highlight ruby %}
    # starting point (line is too long)
    def send_mail(source)
      Mailer.deliver(to: 'bob@example.com', from: 'us@example.com', subject: 'Important message', body: source.text)
    end

    # good
    def send_mail(source)
      Mailer.deliver(to: 'bob@example.com',
                     from: 'us@example.com',
                     subject: 'Important message',
                     body: source.text)
    end

    # good (normal indent)
    def send_mail(source)
      Mailer.deliver(
        to: 'bob@example.com',
        from: 'us@example.com',
        subject: 'Important message',
        body: source.text
      )
    end

    # okay-ish (aligned params and values, hard to read with long params)
    def send_mail(source)
      Mailer.deliver(to:      'bob@example.com',
                     from:    'us@example.com',
                     subject: 'Important message',
                     body:    source.text)
    end
  {% endhighlight %}

## Syntax

* Use `def` with parentheses when there are arguments. Omit the parentheses
  when the method doesn't accept any arguments.
* {% highlight ruby %}
    def some_method
      ...
    end

    def some_method_with_arguments(arg1, arg2)
      ...
    end
  {% endhighlight %}

* Never use `for`, unless you know exactly why. Most of the time iterators
  should be used instead. `for` is implemented in terms of `each` (so you're
  adding a level of indirection), but with a twist - `for` doesn't introduce a
  new scope (unlike `each`) and variables defined in its block will be visible
  outside it.
* {% highlight ruby %}
    arr = [1, 2, 3]

    # bad
    for elem in arr do
      puts elem
    end

    # good
    arr.each { |elem| puts elem }
  {% endhighlight %}

* Never use `then` for multi-line `if/unless`.
* {% highlight ruby %}
    # bad
    if some_condition then
      ...
    end

    # good
    if some_condition
      ...
    end
  {% endhighlight %}

* AVOID the ternary operator EXCEPT in cases where all expressions are trivial.
  Favor the operator, however, over `if/then/else/end` constructs for single
  line conditionals:
* {% highlight ruby %}
    # bad
    result = if some_condition then something else something_else end

    # good
    result = some_condition ? something : something_else
  {% endhighlight %}

* Use one expression per branch in a ternary operator. This also means that
  ternary operators MUST NOT be nested. Prefer `if/else` constructs in these
  cases.
* {% highlight ruby %}
    # bad
    some_condition ? (nested_condition ? nested_something : nested_something_else) : something_else

    # good
    if some_condition
      nested_condition ? nested_something : nested_something_else
    else
      something_else
    end
  {% endhighlight %}

* Avoid multi-line ternary operator. Favor `if/unless` construct.
* Favor `if/unless` usage when you have a single-line body.
* {% highlight ruby %}
    # bad
    if some_condition
      do_something
    end

    # good
    do_something if some_condition
  {% endhighlight %}

* The `and` and `or` keywords should be avoided. Use `&&` and `||` instead.
* Never use `unless` with `else`.  Rewrite with the positive case first.
* Do not use parentheses around `if/unless/while` conditionals.
* Prefer `{...}` over `do..end` for single line blocks.  Avoid using `{...}` for
  multi-line blocks.  Do not use `do..end` while chaining.  Avoid multi-line
  chaining.
* Avoid `return` where not required.  Take advantage of implicit return.

* Use spaces around the `=` operator when assigning default values to method
  parameters:
* {% highlight ruby %}
    # bad
    def some_method(arg1=:default, arg2=nil, arg3=[])
      # do something...
    end

    # good
    def some_method(arg1 = :default, arg2 = nil, arg3 = [])
      # do something...
    end
  {% endhighlight %}

* Using the return value of = (an assignment) is ok.  Avoid using the return
  value in the second part of a conditional:
* {% highlight ruby %}
    # bad
    if (v = array.grep(/foo/)) ...

    # bad
    if v = array.grep(/foo/) && v.length > 1 ...

    # good
    if v = array.grep(/foo/) ...

    # good
    v = array.grep(/foo/)
    if v && v.length > 1 ...

    # also good - has correct precedence.
    if (v = next_value) == "hello" ...
  {% endhighlight %}

* Use `||=` freely to initialize variables.
* Never use `||=` to set boolean values. (Think about what happens when the first
  value is falsey?)
* Never put a space between a method and it's opening parentheses.
* {% highlight ruby %}
    # bad
    f (3 + 2) + 1

    # good
    f(3 + 2) + 1
  {% endhighlight %}

* Following the rule above, if the first argument begins with an open
  parentheses, always use parentheses in the method invocation.
* {% highlight ruby %}
    f((3 + 2) + 1)
  {% endhighlight %}

* Use the new lambda literal syntax (`->`) for single line body blocks.
  Use the `lambda` method for multi-line blocks.

* Prefer `==` over `eql?`.  The stricter comparison is usually not needed.
  * (We use `eql?` sporadically, but should work to remove them.)

* Use guard clauses when you can assert invalid data.  Bail out of the function
  as soon as possible.
* {% highlight ruby %}
    def my_method(argument)
      return unless argument
      do_something_with(argument)
    end
  {% endhighlight %}

* Use `_` for unused block parameters.
* Use `is_a?` or `kind_of?` instead of `===` to check types.  `===` is **not**
  an equality operator ([read the first response here](http://stackoverflow.com/questions/4467538/what-does-the-operator-do-in-ruby)).
    * If you find yourself checking types, you should ask yourself if that's even
      the right approach to solve the problem.

## Naming

* Use `snake_case` for symbols, methods, and variables.
* Use `CamelCase` for classes and modules.
* Use `SCREAMING_SNAKE_CASE` for constants.
* Methods that return a boolean value should end in a question mark.
* {% highlight ruby %}
    def complete?
      art_approved && quantities_submitted
    end
  {% endhighlight %}

* Potentially dangerous methods (ones that modify `self` or arguments) should
  end in an exclamation mark.  Bang methods should only exist if there's a
  safe version available.

## Classes/Modules

* Prefer modules to classes with only class methods.  Classes should be used
  only when it makes sense to create instances out of them.

* Use `def self.method` to define singletons.

* Indent the `public`, `protected`, and `private` methods as much the method
  definitions they apply to. Leave one blank line above them.
* {% highlight ruby %}
    class SomeClass
      def public_method
        ...
      end

      private
      def private_method
        ...
      end
    end
  {% endhighlight %}

## Exceptions

* Do not use exceptions for flow control.
* Avoid rescuing the `Exception` class. Be specific.
* When rescuing exceptions, notify Airbrake using `Airbrake.notify`.

## Collections

* Prefer `%w` over literal array syntax when needing an array of strings.
* Prefer symbols over strings as hash keys.
* Prefer Ruby 1.9 hash syntax, where possible.  When keys are NOT symbols, use
  hash-rocket syntax.

## Strings

* Prefer string interpolation over concatenation.
* Do not pad string interpolation code.
* Prefer double-quoted strings, unless your string contains a quotation mark or
  escape characters that you want to suppress.
* {% highlight ruby %}
    # bad
    name = 'Kotis'

    # good
    name = "Kotis"
    comment = 'Daniel said, "Go Kotis!"'
  {% endhighlight %}

## Regular Expressions

* Be careful with `^` and `$` as they match start/end of line, not string
  endings. If you want to match the whole string use: `\A` and `\z`.
* {% highlight ruby %}
    string = "some injection\nusername"
    string[/^username$/]   # matches
    string[/\Ausername\z/] # doesn't match
  {% endhighlight %}

## Keyword Arguments

* Prefer keyword arguments over "options-hash-as-arguments" style.
* Prefer keyword arguments when a method's arguments are non-obvious when called:
* {% highlight ruby %}
    # instead of this
    def submit_order(user, employee = false)
      ...
    end

    submit_order(user, true) # what does true mean?

    # do this
    def submit_order(user, employee: false)
      ...
    end

    submit_order(user, employee: true)
  {% endhighlight %}

## Testing

Use RSpec, capybara-webkit, FactoryGirl, and fuubar rspec formatter in your
applications.

* Prefer lazy-loading objects with objects that can be shared between tests.
* {% highlight ruby %}
    let(:ups_params) do
      { origin_zip: "98103", weight: "5", shipping_method: "UPS Ground" }
    end

    let(:estore) { FactoryGirl.create(:estore) }
  {% endhighlight %}

* Break tests into contexts, and use whitespace to separate `it`, `let`, and
  `before` statements.  Whitespace should also be used to break spec files into
  readable sections.
  * Use your own discretion.  Just make it readable!

## Miscellaneous

* Default Sublime Text Settings:
* {% highlight ruby %}
    "default_line_ending": "unix",
    "rulers":
    [
      80,
      100
    ],
    "tab_size": 2,
    "translate_tabs_to_spaces": true,
    "trim_trailing_white_space_on_save": true,
    "ensure_newline_at_eof_on_save": true
  {% endhighlight %}
