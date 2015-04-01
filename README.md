# tlks.io : docs

1. [Introduction](#introduction)
2. [Subprojects](#subprojects)
3. [Developer's documentation](#developers-documentation)

This is the documentation for *tlks.io*, a curated and community driven list
of technical talks.

## Introduction

tlks.io is not a single piece of software. It is more a platform based on a
microservices paradigm and designed to minimize the complexity of the system
and maximize the decoupling between its components.

Please, make sure you read our [architecture](arquitecture.md) documents
to see how these different pieces of software, called *microservices*, work
together to keep the system up & running, and their
[configuration & deployment](deploy.md) before you start building or hacking
in one component by yourself.

* [Project's Roadmap](roadmap.md)
* [Platform Arquitecture](arquitecture.md)
    * [What we have now](arquitecture.md#what-we-have-now)
    * [What we want to build](arquitecture.md#what-we-want-to-build)

## Subprojects

For a simpler work organization, the [team](http://tlks.io/about) behind
tlks.io, usually group these components into subprojects according on its
main purpose.

tlks.io current & active subprojects are:

* [front](subprojects/front.md) : Front-End applications & public APIs.
* [core](subprojects/core.md) : Business Logic & core libraries.
* [shiva](subprojects/shiva.md) : Event manager, queue system, producers &
  workers.

## Developer's documentation

Are you willing to help on the development of tlks.io? This is the section
you're looking for:

* [Development guidelines](developers/guidelines.md)
* [Deployment & Configuration](developers/deploy.md)
    * [Requirements](developers/deploy.md#requirements)
    * [Database creation](developers/deploy.md#database-creation)
    * [Full-Text index creation](developers/deploy.md#full-text-index-creation)
    * [Step by Step deployment guide](developers/deploy.md#step-by-step-deployment-guide)
