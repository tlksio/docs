# tlks.io : docs : roadmap

[< Return to index](README.md)

This is the roadmap document for the *tlks.io* project. It describes the
remaining work to do until version *1.0*.

It is a live document, it means that changes on this spec are and will be
comming if it is necessary. Nothing is fixed or closed unless we excplicity
say the contrary. So please put everything in doubt and keep the discussion
alive ;)

This document follows an idea started by Ubuntu, which consists in planning a
great but difficult bug 0 (our 1.0 version) to solve, so all minor versions &
milestones should refer this one and solve an small task and part of it.

## Versioning

For transparency into our release cycle and in striving to maintain backward
compatibility, all project components are maintained under
[the Semantic Versioning guidelines](http://semver.org/). Sometimes we screw
up, but we'll adhere to those rules whenever possible.

We also follow the rule that one issue fixed should be a new minor release, so
expect to have a lot of minor version numbers changes, this will be normal.

## 1.0

Easy or not? ;)

- [*] We rock! ( we always do )
- [] We have been spotted at producthunt.com ( difficult )
- [] We have been spotted on reddit ( easy )
- [] We have at least 1000 registered users
- [] We have at least 25 active users

### 0.1.0

Lets work on a first MVP ( Most Viable Product ) to build a base project to
grow. Minimal features should be:

- [] Popular & Latest talks
- [] RSS popular & latest talks
- [] Browse talks by tag
- [] RSS talks by tag
- [] Search talks
- [] Upvote a talk by registered users
- [] Favorite / Unfavorite talks by registered users
- [] Count views for each talk
- [] Talk detailed view
- [] Share a talk on Twitter ( twitter cards )
- [] Share a talk on Facebook ( facebook opengraph )
- [] Share a talk on Google+ ( G+ snippets )
- [] Share a talk on Pinterest ( Pinterest rich media )
- [] Related talks to another talk snippet ( for detailed view ).
- [] Support only Youtube videos
- [] Auth and user registration throught Twitter OAuth
- [] Publish a new talk ( how to dectect duplicates? )
- [] Comments by disqus
- [] Activity list
- [] Private settings for registered users
- [] Public profile for registered users
- [] Public Profile : Published talks list
- [] Public Profile : Upvoted talks list
- [] Public Profile : Favorited talks list
- [] Corporate pages like About, Terms, Policty, FAQ etc ...

### 0.2.0

We finished our MVP. Now it is time to work on SEO and basic metrics.

Another important part to work on this milestone is on the caché, we must
caché everything we can. We need our MVP as fast as hell!

Finally as a new features we will introduce following and followers to our
users.

- [] SEO ( Jose is your turn )
- [] Google Analytics
- [] Google Webmaster Tools
- [] Metadata!
- [] Microformats!
- [] Users: Following / Followers
- [] Public Profile: Following users list
- [] Public Profile: Followers users list
- [] Caché everything! ( We should discuss a lot this one )
    - [] Redis?
    - [] Varnish?
    - [] Multi-Level custom caché? ( I vote for this one )

### 0.3.0

Enough rock for now, lets make this MVP as solid as Metal. \m/

We will ensure that we have a proper test environment and we will build basic
tests for UNit, Integration and End to End layers. We will also execute those
tests periodically on each component throught *TravisCI* and *coveralls.io*.

As a new feature we will intrdocuce collections of talks to our users.

- [] Collections of talks per user ( see collections at producthunt.com )
- [] Add a talk to a collection from the detailed view
- [] Add a talk to a collection from any list view
- [] Public Profile: Collections list
- [] Proper Unit Testing suite.
- [] Proper End to End Testing suite.
- [] Front-end tests via phantomjs.
- [] Everything on a CI, in our case *TravisCI*
- [] Public code coverage reports using *coveralls.io*

### 0.4.0

Microservices! Microservices!

TODO: This should be discussed!

- [] Support Vimeo videos
- [] Fetch data from youtube and vimeo to fullfill the database asynchronously
  with a separate service.
     - [] ZeroMQ?
     - [] Rabbit?
     - [] NSQ.io?
     - [] Custom?
- [] Separate search from libtlks and front and create:
    - [] libindex ( indexing and searching )
    - [] an api (private ) REST service to search ( with its own caché system )
    - [] implement HAML on this API
    - [] implement HATEOAS on this API

- [] TODO: Think on more services to decouple
    - Separate voting?
    - Separate auth?
    - etc...?

### 0.5.0

Feedback, Notifications & Devop time!

TODO: This should be discussed!

- [] Email notifications to users.
    - [] Sendgrid?
    - [] How to trigger? Queues again?
- [] Just repeat 0.3.0 but for this new microservices arquitecture.
- [] Rethink deploy system.
    - [] Still with Chef? (I like it)
    - [] Docker? ( Our hosting doesn't support it, change to DigitalOcean? )

### 0.6.0

It starts to look as a platform! Now time to think a little bit more,
make this project reliable:

TODO: This should be discussed!

- [] Rethink storage
  At this point using a free MongoDB service could not be enough.
- [] Rethink search
  Same than above, we are using a free bonsai.io instance.
- [] Benchmarks and usage metrics.
    - [] How many users we can support with the current resources?
    - [] How much will cost to escalate it?
    - [] Risks?

### 0.7.0

Ok we have a rock solid platform. Make it pretty, bitch!! :*

TODO: This should be discussed!

- [] New logo
- [] New layout & design
- [] Responsive! At least Desktop, Tablet and High End phones.

### 0.8.0

TODO: This should be discussed!

- [] Just repeat 0.3.0 but for this new layout & design.
- [] Rethink client-side.
    - Continue with Jade & JQuery? ( probably )
    - [] React?
    - [] AngularJS?
- [] Benchmarks and usage metrics on the client side.
     - [] How many users we can support with the current resources?
     - [] How muh will cost to escalate it?
     - [] Risks?

### 0.9.0

TODO: This should be discussed!

- [] Featured collections
- [] Public detailed view for user collections
- [] Landing page / detailed view for featured collections
- [] SEO for Landing feature collection pages
    - [] Subdomain? http://pr0n.tlks.io (don't like it)
    - [] Canonical? http://tlks.io/pr0n-talks ( yes! yes! )
- [] Tune, tweak the platform and prepare the 1.0 version

