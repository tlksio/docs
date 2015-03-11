# tlks.io : roadmap

This is the roadmap document for the *tlks.io* project. It describes the
remaining work to do until version *1.0*.

This document is a live document it means that changes on this spec are and
will be comming if it is necessary. Nothing is fixed or closed unless we
excplicity say the contrary. So please put everything in doubt and keep the
discussion alive.

The document follows an idea started by Ubuntu, planning a great and difficult
bug 0 (our 1.0 version) to solve, so all minor versions & milestones should
refer this one and solve an small task for it.

## Versioning

For transparency into our release cycle and in striving to maintain backward
compatibility, all project components are maintained under
[the Semantic Versioning guidelines](http://semver.org/). Sometimes we screw
up, but we'll adhere to those rules whenever possible.

We also follow the rule that one issue fixed should be a new minor release, so
expect to have a lot of minor version numbers changes, this will be normal.

## 1.0

Easy or not? ;)

* We rock! ( we always do )
* We have been spotted at producthunt.com ( difficult )
* We have been spotted on reddit ( easy )
* We have at least 1000 users

### 0.1.0

Lets work on a first MVP ( Most Viable Product ) to build a base project to
grow. Minimal features should be:

* Popular & Latest talks
* Browse talks by tag
* Search talks
* Upvote / Favorite talks
* Talks views
* Auth throught Twitter
* Publish talk ( who to dectect duplicates? )
* Support Youtube & Vimeo videos
* Fetch data from youtube and vimeo to fullfill the database
* Comments by disqus
* Activity list
* Public profile for registered users
* Public Profile : Published talks list
* Public Profile : Upvoted talks list
* Collections of talks per user ( see collections at producthunt.com )
* Public Profile: Collections list
* Collections landing page ( see collections at producthunt.com )
* Corporate pages like About, Terms, Policty, FAQ etc ...

### 0.2.0

Now let's make this MVP fast as hell!


* SEO ( Jose is your turn ).
* Caché everything ( We should discuss a lot this one )
    * Redis?
    * Varnish?
    * Multi-Level custom caché? ( I vote for this one )

### 0.3.0

Enough rock for now, lets make this MVP as solid as Metal. \m/

* Proper Unit Testing suite.
* Proper End to End Testing suite.
* Front-end tests via phantomjs.
* Everything on a CI, in our case TravisCI.

### 0.4.0

Microservices! Microservices!

* Separate search from libtlks and front and create:
    * libindex ( indexing and searching )
    * an api (private ) REST service to search ( with its own caché system )
    * implement HAML on this API
    * implement HATEOAS on this API

* TODO: Think on more services to decouple

### 0.5.0

* Just repeat 0.3.0 but for this new microservices arquitecture.
* Rethink deploy system.
    * Still with Chef?
    * Docker?

### 0.6.0

It starts to look as a platform! Now time to think a little bit more,
make this project reliable:

* Rethink storage ( at this point using a free MongoDB service could not be
  enough ).
* Rethink search ( same than above, we are using a free bonsai.io instance )
