---
collection: git
layout: page-with-sidebar
title: Git - Branches
sidebar_title: Branches
permalink: /docs/git/branches/
---

# Git - Branches

## Hotfixes

Hotfix branches should contain code that fixes errors in currently deployed code
(the `master` branch).

Branch names should always start with a *hotfix-* prefix. They should also:

- Be 3-5 words
- Descriptive of the problem
- Not repetitive
- Always use dashes as word separators, even in class/property names
  (no snake_case or CamelCase)

Good names:

- *hotfix-remove-cart-caching*
- *hotfix-contact-deletion-bug*
- *hotfix-showcase-premature-caching*
- *hotfix-update-database-type*

Okay names:

- *hotfix-price-importer-bug-fix* (repetitive and unclear what the "bug" is)

Not so good names:

- *hotfix-showcase-request-prematurely-setting-ready-to-approve*
- *hotfix-ShowcaseRequest-updated_at*

## Features

Feature branches should encompass *complete* features.

There is no limit to the number of issues a branch & PR resolves, as there might be
multiple issues for a given feature.

However, you **should not** combine multiple features into a single branch.

Branch names should always start with a *feature-* prefix.  They should also:

- Be 3-5 words
- Descriptive of the problem
- Not repetitive
- Always use dashes as word separators, even in class/property names
  (no snake_case or CamelCase)

Good names:

- *feature-30dtp-updates*
- *feature-fix-showcase-product-links*
- *feature-remove-id-dropdown*
- *feature-copy-product-associations*

Okay names:

- *feature-removing-extra-require*
  - Why? This removed one line of code that wasn't causing an issue.  Not a feature.

Not so good names:

- *feature-address-styling*
  - Why? This branch actually adds a way to skip address validation.
- *feature-add-finalized_at-to-Order*
  - Why? Uses mixed case for properties and classes. Always use lowercase and dashes.

___

[Previous Page: Git - Introduction]({{ site.baseurl }}/docs/git/) &nbsp; | &nbsp;
[Next Page: Git - Issues]({{ site.baseurl }}/docs/git/issues/)
