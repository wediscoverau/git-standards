# Git commit standards

This documents the standard for git commits across all We Discover projects.
Information on how to add and enforce this on new projects is included at the
bottom.

# Contributing

Anyone is welcome to contribute anything (features, bugfixes, code style
improvements, etc.) to this codebase. To keep things clean and easy to manage,
we've adopted the following conventions:

1. No merge commits – you'll only have the option to do a rebase merge (you
   shouldn't have to do anything differently for this).
2. One commit per body of work
3. Commit messages should follow the git conventions (50 characters first line
   summary, 72 characters per line after that).
4. We're following the Airbnb styleguide — https://github.com/airbnb/javascript

## Few commits

In the above list, it says "one commit per body of work". This will often
translate to a single JIRA issue (but doesn't always – sometimes it's just
easier to do solve multiple issues with a single chunk of code). This will
often mean that there's only a single commit in a PR, but multiple commits are
fine as long as they are separate bodies of work.

## Good commit messages

Of course, this is subjective, but we've decided to give the Karma project's guidelines for commit
messages a whirl. These are likely similar to many other projects' guidelines.
Below is a summary. The full details are available here:
[http://karma-runner.github.io/2.0/dev/git-commit-msg.html](http://karma-runner.github.io/2.0/dev/git-commit-msg.html).

Karma's guidelines were based on Angular's [git commit message
conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#).

### Format of the commit message

```
<type>(<scope>): <subject>

<body>
```

Example:
```
feat: (home-page) hero carousel
- Added a new hero carousel component
```

#### Type

> - feat (new feature for the user, not a new feature for a build script)
> - fix (bug fix for the user, not a fix to a build script)
> - docs (changes to the documentation)
> - style (formatting; no production code change)
> - refactor (refactoring production code, e.g., renaming a variable)
> - test (adding missing tests, refactoring tests; no production code change)
> - chore (updating build tasks, etc.; no production code change)

#### Scope

Scopes are just human-friendly descriptions of the sections of the codebase
you're working on. You can come up with anything that makes sense, but add it
to this list when you do.

- *a scope*
- *another scope*

> The `<scope>` can be empty (e.g., if the change is global or difficult to
> assign to a single component) in which case the parentheses are omitted.

#### Message body

Karma provides some guidelines on how the message body should be written:

> - Uses the imperative, present tense: "change" not "changed" nor "changes"
> - Includes the motivation for the change and contrasts with previous behaviour

These guidelines are good, but do not need to be adhered to strictly.

# Adding these standards to a project

## `CONTRIBUTING.md`

The contents of this file (apart from this section) can be copied into a
`CONTRIBUTING.md` file in each of our repos, which is supported by GitHub and
will be surfaced when new PRs are being opened.

Before committing a new `CONTRIBUTING.md`, be sure to update the list of scopes
above and add a link to the relevant style guide.

## Building in travis

Run this in your project's repo:

```
npm init
npm install --save-dev @commitlint/{config-conventional,cli,travis-cli}
```

And add the following to your `.travis.yml` file:

```
before_script:
  - npm install

script:
  - ./node_modules/.bin/commitlint-travis
```

