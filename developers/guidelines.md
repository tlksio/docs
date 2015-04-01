# tlks.io : Developer guidelines

[TOC]

## Introduction

This document defines a list of *good practices* that every developer should
follow. Please read them carefully.

Don't worry because they are not too complicated to follow and put them in
practice.

In fact there is a few required practices in case you are willing to
contribute to tls.io and we specifically express these in this documentation.
All other practices are optional.

Anyone can ask to another member or contributor to provide optional
requirements if he considers that it is needed for the clarification or
reliability of the system.

If a current and active team member asks you to provide some extra work on a
issue or change you've been made consider yourself obligated to do it ( or
at least provide reasons to do not ).

Also in case you're working on more than one thing at once, those
requests must have higher priority so finish them first.

## Development process

In order of precendence always work on existing
[issues](https://github.com/tlksio/front/issues) before spending hours on
new things.

If you have an idea for the future and it is not planed on the global
[roadmap](http://github.com/tlksio/docs/roadmap.md) write its documentation and
reasons why its needed and propose it to the team. Go and ping to a team member developer and ask him to disscuss it. Good luck! ;)

## Source code testing conventions

*tlks.io* team follows a TDD & BDD workflow on all of the components that
belongs to the platform.

For unit and behaviour tests our module of choice is
[MochaJS](http://mochajs.org) and
[Istanbul](http://github.com/gotwarlost/istanbul) is used for code coverage
data generation. In UI and end-to-end tests we use
[PhantomJS](http://phantomjs.org) and [CasperJS](http://casperjs.org).

Each component must describe how to run its tests suite on its own
documentation.

In top of this, we use [TravisCI](http://travis-ci.org) &
[Coveralls](http://coveralls.io) services to continuous integration and
code coverage report generation.

On each component both *develop*, *master* & *release* branches must
be tested and its code coverage report generated after each commit. It's is
optional for the developer to run the test suite on its development branches.

## Source code lint conventions

Please, lint your code before pushing it to *develop* or *master*. And no
pull request must be accepted if it contains unlint source code.

We use [JSHint](http://jshint.org) for Javascript linting and JSON files and [CSSlint](http://csslint.org) to lint our Style sheets.

Each component must describe how to lint its own code on its own
documentation.

## Documentation conventions

This is really really important! Do you see that this project has a lot of
documentation. isn't it? That's not just a coincidence!

We strongly believe that good documentation reflects directly on the
quality of a project, so we document everything we do and why we did in that
particular way.

So please, make sure you document any decision you made while working on
any of our components. No algorithm, library or even method should be
present on the project if its not documented. And of course no new code
will be accepted if its not followed by its documentation.

In case you have any question about the platform, follow this steps:

1. Check general current documentation project files for undocumented topics.
2. Check specific component documentation in case you didn't found anything.
3. Ask to the team if you still didn't find anything. ;)

## Version number and source code management conventions

We strongly recomend to all team members and contributors to use
[git-flow](http://atlassian.com/gitflow) with their work. That tool helps
a lot because:

1. We strictly follow [SemVersion](http://semver.org) recomendations.
2. Every resolved issue must be followed by a new stable release and minor
  version bump.
3. Only the latest release version branch is deployed in production.

If you need to deploy your work in production please ask to one of the
team members and provide him the release number you want/need to deploy.
