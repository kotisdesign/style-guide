---
collection: git
layout: page-with-sidebar
title: Git - Pull Requests
sidebar_title: Pull Requests
permalink: /docs/git/pull-requests/
---
# Git - Pull Requests

## Creating a Pull Request

Pull requests should be created any time you want to merge code into the application.

Ensure when creating the pull request that you propose your branch into the correct
place:

- *Feature* branches -> `develop`
- *Hotfix* branches -> `master`

## Naming

Pull requests should be named appropriately, to provide a quick summary when looking
at the history of a repository.

The name of a pull request should **describe the feature being proposed**.  Often,
this is more than the branch name or the first commit name, which are Github's
default suggestions.

**Examples:**

- GOOD:
  - Hides "No ISR List" header if there is nothing in the table
  - Allow HTML in product descriptions
  - Add asp response message to order
  - Makes it so pure buttons use black as a text color
- OKAY:
  - Feature resolve broken product image uploads
    (GOOD: "Resolves broken product image uploads")
- NOT SO GOOD:
  - Feature pure css

## Expectations

When proposing a pull request, there are certain expectations that must be met
before they are evaluated, reviewed, and merged in, which are described in this
section.

**Pull requests should be proposed into the appropriate branch:**

- Feature branches should be proposed into `develop`, and hotfix branches into
  `master`.
- Incorrectly proposed branches will be closed before any commenting takes place.

**Pull requests should be able to automatically merge:**

- Before creating a PR, **rebase** your PR with the most current copy of the branch
  your proposing into.
{% highlight bash %}
  git fetch origin
  git checkout <your-feature-branch>
  git rebase develop
{% endhighlight %}
- Resolve any conflicts, remembering that the new develop branch is the *current
  working branch*.
- Test your feature after the rebase and ensure it works as desired.

**The last commit of your pull request should be <span class="other-green">green
  on Sempahore</span>.**

**The descriptions should be *descriptive*:**

- Summarize the feature you are proposing to merge in.
- Include any potential issues, considerations that need to be taken,
  and questions or concerns that you have encountered in development.
- Include the issues the PR is closing: "Fixes #123, #124, #125" or "Closes #123,
  #301"
  - NOTE: this does not automatically close issues. Issue numbers should be
    formatted properly when merging `develop` into `master`, or vice versa for
    hotfixes.
- Descriptions should not just be issue numbers.
- Descriptions should not be blank.
- If you have done something at the request of another, include that:
  - "Per my conversation with @becker1, we decided to do X instead of/in
    addition to Y."

## Code Review

All pull requests and code are subject to review.  Code review is designed to
ensure that the code is high quality and safe for production.  A primary goal
of code review is for both the reviewer and reviewee to learn new techniques and
improve overall coding ability.

- Initial code review should occur within three business days.
- Generally, the review will not focus on style comments, instead focusing on test
  issues, logic issues, organizational issues, etc.
- All comments should be addressed with either:
  - A code change
  - A comment with questions/concerns/etc.
- Perform a self-review when creating the PR:
  - During the PR creation stage, you'll see the file changes diff.
  - Take some time and review your own code first. If you see problems, make
    changes *before* submitting the PR for review.
  - *Self-review saves a lot of time!*

## Example Pull Requests

### Good #1

![Good PR Example 1]({{ site.baseurl }}/assets/images/git-pull-requests-good-1.png)

Why is this good?

- Name is concise and accurately describes the feature being proposed
- Description summarizes the feature in detail, includes potential issues and
  concerns that may arise in the future, and describes which issues it closes
  and addresses.
- Contains a complete feature.

### Good #2

![Good PR Example 2]({{ site.baseurl }}/assets/images/git-pull-requests-good-2.png)

Why is this good?

- Name accurately describes the feature being proposed
- Description summarizes the feature being added and describes which issue it closes.
- Contains a complete feature.

### Good #3

![Good PR Example 3]({{ site.baseurl }}/assets/images/git-pull-requests-good-3.png)

Why is this good?

- Name accurately describes the feature being proposed
- Description details the feature being added and describes which issue it closes.
- Addresses potential issues that may arise: "I'm not sure what unintended
  consequences..."

___

### Okay

![Okay PR Example]({{ site.baseurl }}/assets/images/git-pull-requests-okay.png)

Why is this okay?

- Name generally addresses the problem
- Description includes the issues this feature fixes, and addresses considerations
  that must be taken before merging.

Possible improvements:

- Name simply uses the branch name (a Github default)
  - Removing "feature" is less duplicative
- Description does not explain what the issues are that this feature fixes.
  - It's nearly impossible to tell by reading this description what the branch
    is actually trying to accomplish.
- Use markdown formatting for the "IMPORTANT" text.
  - Basic markdown formatting can go a long way in terms of readability of both
    issue and pull request summaries.

___

### Not So Good

![Not So Good PR Example]({{ site.baseurl }}/assets/images/git-pull-requests-notsogood.png)

Why is this not so good?

- Name is unclear.  What is this feature/PR doing?
- No description.  Again, what is this feature doing?

Improvements:

- Update the name of the PR to better describe *what* this PR does.
  - "Implements PureCSS Framework"
- Add a description
  - Explain what we're doing and why
  - Links to specific issues still require someone to look into the issues to
    figure out what's going on.  Ideally, reviewers look at the issues to determine
    whether the PR actually resolves the issue, not to determine what the PR does.
  - The description of the issue linked in this PR has no description.  One should
    be added.

___

[Previous Page: Git - Issues]({{ site.baseurl }}/docs/git/issues/)
