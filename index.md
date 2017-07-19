---
title: Conventional Commits 1.0.0-beta.1
redirect_from: /lang/en/
---

# Conventional Commits 1.0.0-beta.1

## Summary

As an open-source maintainer, squash feature branches onto `master` and write
a standardized commit message while doing so.

The commit message should be structured as follows:

---

```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```
---

<br />
The commit contains the following structural elements, to communicate intent to the
consumers of your library:

1. **fix:** a commit of the _type_ `fix` patches a bug in your codebase (this correlates with [`PATCH`](http://semver.org/#summary) in semantic versioning).
2. **feat:** a commit of the _type_ `feat` introduces a new feature to the codebase (this correlates
  with [`MINOR`](http://semver.org/#summary) in semantic versioning).
3. **BREAKING CHANGE:** a commit that has the text `BREAKING CHANGE:` at the beginning of its optional body or footer section introduces a breaking API change (correlating with [`Major`](http://semver.org/#summary) in semantic versioning). A breaking change can be
  part of commits of any _type_. e.g., a `fix:`, `feat:` & `chore:` types would all be valid, in addition to any other _type_.

<br />
A scope may be provided to a commit's type, to provide additional contextual information and
is contained within parenthesis, e.g., `feat(parser): adds ability to parse arrays`.

Commit _types_ other than `fix:` and `feat:` are allowed, for example [the Angular convention](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit) recommends `docs:`, `style:`, `refactor:`, `perf:`, `test:`, `chore:`, but these tags are
not mandated by the conventional commits specification.

## Introduction

In software development, it's been my experience that bugs are most often introduced
at the boundaries between applications. Unit testing works great for testing the interactions
that an open-source maintainer knows about, but do a poor job of capturing all the
interesting, often unexpected, ways that a community puts a library to use.

Anyone who has upgraded to a new patch version of a dependency, only to watch their
application start throwing a steady stream of 500 errors, knows how important
a readable commit history (and [ideally a well maintained CHANGELOG](http://keepachangelog.com/en/0.3.0/)) is to the ensuing
forensic process.

The Conventional Commits specification proposes introducing a standardized lightweight
convention on top of commit messages. This convention dovetails with [SemVer](http://semver.org),
asking software developers to describe in commit messages, features, fixes, and breaking
changes that they make.

By introducing this convention, we create a common language that makes it easier to
debug issues across project boundaries.

## Conventional Commits Specification

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

1. A *type* is a string token, e.g. `feat` or `fix`.
2. A *scope* is a string token describing a section of the codebase enclosed in parenthesis, e.g. `(parser)`.
3. A *description* is a short description of the pull request, e.g. `array parsing issue when multiple spaces were contained in string`.
4. A commit message MUST start with a *type*.
5. The *type* `feat` MUST be used when a commit adds a new feature to your application
  or library.
6. The *type* `fix` MUST be used when a commit represents a bug fix for your application.
7. An optional *scope* MAY be provided immediately after the *type*. 
8. A colon `:` and a space, followed by a *description* MUST be included after *scope*, when provided, or *type*, when *scope* is ommited.
9. A longer commit *body* MAY be provided after the short description. The *body* then MUST
   begin one blank line after the description.
10. A *footer* MAY be provided one blank line after the *body*. The footer then SHOULD contain
   additional meta-information about the pull-request (such as the issues it fixes, e.g., `fixes #13, #5`).
11. Breaking changes MUST be indicated at the very beginning of the *footer* or *body* section of a commit. A breaking change MUST consist of the uppercase text `BREAKING CHANGE`, followed by a colon and a space.
12. A description MUST be provided after the `BREAKING CHANGE: `, describing what
  has changed about the API, e.g., `BREAKING CHANGE: environment variables now take precedence over config files.`
13. Types other than `feat` and `fix` MAY be used in the commit message.

## Why Use Conventional Commits

* Automatically generating CHANGELOGs.
* Automatically determining a semantic version bump (based on the types of commits landed).
* Communicating the nature of changes to teammates, the public, and other stakeholders.
* Triggering build and publish processes.
* Making it easier for people to contribute to your projects, by allowing them to explore
  a more structured commit history.

## FAQ

### How should I deal with commit messages in the initial development phase?

We recommend that you proceed as if you've an already released product. Typically *somebody*, even if its your fellow software developers, is using your software. They'll want to know what's fixed, what breaks etc.

### What do I do if the commit conforms to more than one of the commit types?

Go back and make multiple commits whenever possible. Part of the benefit of Conventional Commits is its ability to drive us to make more organized commits and PRs.

### Doesn’t this discourage rapid development and fast iteration?

It discourages moving fast in a disorganized way. It helps you be able to move fast long term across multiple projects with varied contributors.

### Might Conventional Commits lead developers to limit the type of commits they make because they'll be thinking in the types provided?

Conventional Commits encourages us to make more of certain types of commits such as fixes. Other than that, the flexibility of Conventional Commits allows your team to come up with their own types and change those types over time.

### How does this relate to SemVer?

`fix` type commits should be translated to `PATCH` releases. `feat` type commits should be translated to `MINOR` releases. Commits with `BREAKING CHANGE` in the commits, regardless of type, should be translated to `MAJOR` releases.

### How should I version my extensions to the Conventional Commits Specification, e.g. `@jameswomack/conventional-commit-spec`?

We recommend using SemVer to release your own extensions to this specification (and
encourage you to make these extensions!)

### What do I do if I accidentally use the wrong commit type?

#### When you used a type that's of the spec but not the correct type, e.g. `fix` instead of `feat`

Prior to merging or releasing the mistake, we recommend using `git rebase -i` to edit the commit history. After release, the cleanup will be different according to what tools and processes you use.

#### When you used a type *not* of the spec, e.g. `feet` instead of `feat`

In a worst case scenario, it's not the end of the world if a commit lands that does not meet the conventional commit specification. It simply means that commit will be missed by tools that are based on the spec.

### Do all my contributors need to use the conventional commit specification?

No! If you use a squash based workflow on Git lead maintainers can cleanup the commit messages as they're merged—adding no workload to casual committers. A common workflow for this is to have your git system automatically squash commits from a pull request and present a form for the lead maintainer to enter the proper git commit message for the merge.

## About

The Conventional Commit specification is inspired by, and based heavily on, the [Angular Commit Guidelines](https://github.com/angular/angular.js/blob/master/CONTRIBUTING.md#commit).

The first draft of this specification has been written in collaboration with some of the
folks contributing to:

* [conventional-changelog](https://github.com/conventional-changelog/conventional-changelog): a
  set of tools for parsing conventional commit messages from git histories.
* [unleash](https://github.com/netflix/unleash): a tool for automating the
  software release and publishing lifecycle.
* [lerna](https://github.com/lerna/lerna): a tool for managing monorepos, which grew out
  of the Babel project.

## Projects Using Conventional Commits

* [yargs](https://github.com/yargs/yargs): everyone's favorite pirate themed command line argument parser.
* [istanbuljs](https://github.com/istanbuljs/istanbuljs): a collection of open-source tools
  and libraries for adding test coverage to your JavaScript tests.
* [standard-version](https://github.com/conventional-changelog/standard-version): Automatic versioning and CHANGELOG management, using GitHub's new squash button and the recommended Conventional Commits workflow.

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)

_want your project on this list?_ [send a pull request](https://github.com/conventional-changelog/conventionalcommits.org/pulls).

## License

[Creative Commons - CC BY 3.0](http://creativecommons.org/licenses/by/3.0/)
