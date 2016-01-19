---
layout: page
title: Front End
permalink: /docs/frontend/
---

# Front End

This is an initial version of a front end style guide. This is going to be somewhat fluid at the
start and we will most likely need to add, remove and change aspects of this as we progress.
First and foremost if something ever looks bad, please say something.

## Font Face

* `font-family: 'Open Sans', sans-serif;`

## Font Size

* Use standard Pure font sizes, which start at 1em and uses these sizes for headers:
  * `<h1>2em</h1>`
  * `<h2>1.5em</h2>`
  * `<h3>1.17em</h3>`
  * `<h4>1em</h4>`

## Links

* Primary link color is cyan blue #<span class="primary-blue">00a6ce</span> with a hover of #<span class="hover-blue">007da4</span>

## Forms

* Generally try to use Pure's "[aligned form](http://purecss.io/forms/#aligned-form)"
* Corners of form input fields should be .125em rounded
* Checkboxes and radio buttons should always use a <label> tag around the label text, so that you
can click on the words and not just the button

### Form Labels

* Right align text against the input box/form field, padding-right of .5em
* "Capitalize First Letters", "Unless somehow the label is a sentence"
* Font color should be the same as the surrounding text on the page
* Do not use colons unless there is a clear reason to
* Generally avoid using placeholder text on an input field as the label. Once you start typing or
if there are form errors, it is not clear what the label is
  * Exceptions are potentially ok with a very small number of fields or if the fields are obvious,
  like a login page with only email and password
* If every field is required, do not use a required indicator
  * If almost all fields are required, put “(optional)” after the labels for the few optional fields
  * If there is a mix of required and optional fields, put an nbsp; and asterisk after the label
  for the required field in the same color as the label

## Buttons

* .125em rounded corners
* "Capitalize First Letters", "Unless somehow the button is a sentence"
* Font-weight: try to use "normal" where you can
* Unless there is a specific reason to use icons within a button, let's not use them
* Use standard Pure hover properties

### Button Colors

* Primary - orange (<span class="primary-orange">ff4c00</span>)
  * Main action buttons like "save"; most POST actions
* Primary - cyan blue (<span class="primary-blue">00a6ce</span>)
  * Most GET actions; or POST actions with only light edits and/or if there is already an orange
  button and we need to differentiate
* Secondary - gray (<span class="secondary-gray">999</span>)
  * GET actions if there is already a cyan button
* Other - red (<span class="other-red">f6323e</span>)
  * Not a standard Kotis color, but ok to use if we need a "delete" or "cancel" or just general
  warning button
* Other - green (<span class="other-green">00b44f</span>)
  * Try not to use this unless we need to, not a standard Kotis color
* Try to use the above color concepts very closely for internal uses. On an external page if the
buttons look bad or conflict with other graphics, please say something

## Tables (data grids)

* Header background is #777, with white bold text
* Outside border and left/right cell borders should be #cbcbcb [Pure default]
  * Header borders should be #999
* Content should be left justified within a cell
* Content should generally have padding of 0.5em
* Alternate rows with background of #f2f2f2 and #fff [both Pure defaults]
  * (Normally) Every other row, OR
  * (Occasionally) Alternate based on groups of rows using the “sort by” field, ie if it’s sorted
  by date then everything with one date could be the same color and it switches at the next date.
  This is scenario specific, don’t use this option by default but we may want it in some cases. In
  this case we should add horizontal lines on each table row in #999.

## Pagination

* "Previous" and "Next" should always show up, but "previous" is disabled on first page and "next"
is disabled on last page
* Non-disabled buttons: #333 font color, #999 border, #777 border on hover
* Disabled buttons: #999 font color, #ddd border, no hover
* Current page has #777 background and white text
* Padding: 0.25em, 0.5em;
* No italics
* If the pagination is visually within some kind of horizontal bar (see the "design archive" for
example)
  * Don’t show the borders around the links except on hover
  * Don’t use background color (or white text) on current page

## Dates

* When displaying dates, show 2 digit years
* Don’t display leading zeroes on days/months (ie **4/1/15** vs not 04/01/15 and not 4/1/2015)
* Use jquery datepicker

## Flash Messages

* Success messages should have a full-width green background (<span class="other-green">00b44f</span>)
  * black text
  * no border
  * .5em padding
  * .125em rounded corners
* Failure/warning messages should be the same except red background (<span class="other-red">f6323e</span>)

## Headers

Still working on this

## Standards Will Change

Make sure to share styles among all pages, so that changes can be done easily
from a single place.