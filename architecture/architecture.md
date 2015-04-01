# tlks.io : Platform arquitecture

This is the document that describes the arquitecture of tlks.io.

## What we have now

Current the project consists on, this architecture will be maintained only
until version 0.1.0. See the [roadmap](roadmap.md) for more information.

* 1 Core library for the business logic
  [libtlks](https://github.com/tlksio/libtlks)
* 1 Front end web app that consumes core libraries
  [front](https://github.com/tlksio/front)
* 2 Tools [cli](https://github.com/tlksio/cli) and
  [db](https://github.com/tlksio/db) to manage the index, and the database and
  consumes core libraries.
* 2 Tools [vagrant](https://github.com/tlksio/vagrant) and
  [chef](https://github.com/tlksio/chef() to manage the deployment.

## What we want to build

And we want an architecture like this one we will have this architecture once
we reach the 1.0 version. See the [roadmap](roadmap.md) for more information.

* N Core libraries decoupled by purpose or type of work to do.
    * **libtlks:** Handles everything related with talks.
    * **libindex:** Handles everything related with the index & the search.
    * **libusers:** ?
    * **libcache:** ?
    * Others?
* N Microservices that export private APIs and consumes core libraries:
    * **Auth:** credentials storage REST API
    * **Search:** Indexing & Searching API
    * **Talks / Collections:** Database CRUD REST API
    * **Caché:** Multiple levels & agnostic caché API
    * **Voting / Favoriting talks:** Asyncronous, queued and evented!
    * etc ..
* Front end web app that consumes private APIs
  [front](https://github.com/tlksio/front)
* 2 Tools [cli](https://github.com/tlksio/cli) and
  [db](https://github.com/tlksio/db) to manage the index, and the database
  and consumes private APIs.
* 2 Tools [vagrant](https://github.com/tlksio/vagrant) and
  [chef](https://github.com/tlksio/chef() to manage the deployment.

