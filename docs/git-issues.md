---
layout: page-with-sidebar
title: Git - Issues
permalink: /docs/git/issues/
---

# Git - Issues

## Creating an Issue

Any time you notice a problem that is likely affecting multiple users, you should
create an issue on Github.

Name the issue *as descriptively as possible*, but it is important to **be concise**.

The description of the issue should be used and should assist whoever may work
on the problem in the future:

- Include what you did to encounter the issue and steps to recreate the problem
- Include any email text and/or screenshots from the user
- Reference related issues or things you've noticed that might be contributing
to the problem
- Try to stay focused on the issue at hand.

**Please limit issues to single features/bugs.**

## Example Issues

### Good

![Good Issue Example]({{ site.baseurl }}/assets/images/git-issues-good.png)

Why is this good?

- Name contains the action that needs to be taken
- Issue describes what, when, and where the changes should take place

Potential improvements, though not necessary:

- Mention where in the footer the link to the FAQ should go.
  - Should it be before or after the "Contact Us" or "Powered by Kotis Design"?
- Specify the URL to the FAQ page.
  - The issue suggests we have a FAQ, but it's not clear where exactly this is.

___

### Okay

![Okay Issue Example]({{ site.baseurl }}/assets/images/git-issues-okay.png)

Why is this okay?

- The name of the issue contains the problem in a concise format.
  - But, it does not say *what* we want to change.
- The description contains information about what the problem is, when it occurs,
  and where the problem takes place.
  - However, the description is a tad confusing to interpret.

Improvements:

- Change the name to reflect *what* we want to do.
- Add red drawing lines using a basic paint program to point out the problem.
- Move the text from the bottom of the issue to the top, ahead of the screenshot.

___

### Not So Good

![Not So Good Issue Example]({{ site.baseurl }}/assets/images/git-issues-notsogood.png)

Why is this not so good?

- The name of the issue is not clear.  It does not say what the problem is OR
  what we want to do.
- The description should not start with a question.
- In addition to the name, the description does not say what we need to do, where
  a problem is occurring, or whether there is even work to be done.

Improvements:

- Fix the name.  It should say *what* we want to do.
- Update the description to specify what the problem is, what solutions are available,
  and what actions we need to take.  If there are none, there shouldn't be an issue.
- If an "issue" is a discussion, the name and description should reflect that,
  and a label should be added indicating so.

___

[Previous Page: Git - Branches]({{ site.baseurl }}/docs/git/branches/) &nbsp; | &nbsp;
[Next Page: Git - Pull Requests]({{ site.baseurl }}/docs/git/pull-requests/)
