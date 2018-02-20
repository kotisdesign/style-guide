---
collection: git
layout: page-with-sidebar
title: Git
sidebar_title: "Introduction and<br> General Concepts"
permalink: /docs/git/
---
# Git - Introduction and General Concepts

This style guide is meant to describe how Kotis uses Git and GitHub, and outlines
suggestions and expectations applicable to code development across all of our
applications.  Each major section will have real-world examples of good and
not-so-good commits, issues, and pull requests.

One question that may come up is:

## Why do we do this?

The main goals of coming up with a standard set of practices for GitHub are quite
simple:

- **To improve and enhance our skillsets**
  - Learn to write better code
  - Learn to identify code that could be improved
  - Ensure future developers can tell what happened before them
- **To prevent unwanted code from getting into the application**
  - There have been commits made directly into `develop` when we were merging
    pull requests
  - This could result in non-working code getting deployed into production.
- **To save time down the road**
  - Ensuring quality code now prevents having to spend more time in the future
    debugging and attempting to figure out what happened (potentially years earlier!)

While looking through this guide, please keep these goals in mind, and understand
that this has been developed with both *self* and *team* improvement in mind.

## General Concepts

- Modified version of "Git Flow"
- Two branches per repository:
  - "master"
  - "develop"
- *ALWAYS* make sure to `git fetch` or `git pull` before creating new branches
- **DO NOT COMMIT DIRECTLY TO EITHER BRANCH**

## Commit Messages

Commit messages are the backbone of describing a code change.  Commit early and
often, especially when discrete portions of a feature are completed.  Because
of its proxmity to the code, commit messages are very important in determining
what the code is doing.  Messages should conform to the following:

- Always be in the present tense
- Always be an action
- Use lowercase, except when referencing object names
- BE DESCRIPTIVE
  - The first line of a commit message should be 80 characters or less, but can
    contain additional lines of explanation.

Good names:

- "alters ProductImage structure so it can directly store urls"
- "fixes failing raw product spec"

Not so good names:

- "CR Feedback"
  - Not present tense; Not an action; Does not indicate what is actually
    happening in the commit
- "adds inline style"
  - Does not indicate what is actually happening -- *where* are we adding the style?

## Feature vs Hotfix Branches

*Feature* branches should contain a complete set of code changes need to implement
or remove a "feature", as described in a GitHub issue.

*Hotfix* branches should contain code that fixes errors in currently deployed
code that is actively preventing users from using the application.  Hotfixes may
also include fixes to errors that expose security risks.

- Examples include (but are not limited to):
  - Broken forms
  - Missing/failing user authentication
  - Invalid routes

## `master` branch

The master branch is the *currently deployed* production code.

New *features* **should not** be created from this branch.

*Hotfix* branches, which contain fixes to errors that are actively preventing
users from using the application, **should** be created and proposed into this
branch.

## `develop` branch

This is *production-ready* code, but may or may not be live.

All *features* should be created from this branch:
{% highlight bash %}
git checkout -b <feature-branch-name> develop
{% endhighlight %}

Do not merge your own PRs into `develop`, and ***take extreme care*** *to avoid
committing directly to this branch*.

You should:

- Create pull requests (PRs) for new features into this branch
- Create PRs for non-emergency "hotfix" features, including:
  - Quick style changes
  - Non-blocking small fixes with few or no tests

___

[Next Page: Git - Branches]({{ site.baseurl }}/docs/git/branches/)
