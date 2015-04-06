# tlks.io : docs : roadmap

[< Return to index](README.md)

This is the roadmap document for the *tlks.io* project. It describes the
remaining work to do until version *1.0*.

It is a live document, it means that changes on this spec are and will be
comming if it is necessary. Nothing is fixed or closed unless we excplicity say
the contrary. So please put everything in doubt and keep the discussion
alive ;)

This document follows an idea started by Ubuntu, which consists in planning a
great but difficult bug 0 (our 1.0 version) to solve, so all minor versions &
milestones should refer this one and solve an small task and part of it.

## Versioning

For transparency into our release cycle and in striving to maintain backward
compatibility, all project components are maintained under
[the Semantic Versioning guidelines](http://semver.org/). Sometimes we screw
up, but we'll adhere to those rules whenever is possible.

We also follow the rule that one issue fixed should be a new minor release, so
expect to have a lot of minor version numbers changes, this will be normal.

## 1.0

Easy or not? ;)

- [x] We rock! ( we always do )
- [ ] We have been spotted at producthunt.com ( difficult )
- [ ] We have been spotted on reddit ( easy )
- [ ] We have at least 1000 registered users
- [ ] We have at least 25 active users

### 0.1.0

Lets work on a first MVP ( Most Viable Product ) to build a base project to
grow. Minimal features should be:

- [x] Popular & Latest talks
- [x] RSS popular & latest talks
- [x] Browse talks by tag
- [x] RSS talks by tag
- [x] Search talks
- [x] Upvote a talk by registered users
- [x] Favorite / Unfavorite talks by registered users
- [x] Count views for each talk
- [x] Talk detailed view
- [x] Share a talk on Twitter ( twitter cards )
- [x] Share a talk on Facebook ( facebook opengraph )
- [x] Share a talk on Google+ ( G+ snippets )
- [x] Share a talk on Pinterest ( Pinterest rich media )
- [x] Related talks to another talk snippet ( for detailed view ).
- [x] Support only Youtube videos
- [x] Auth and user registration throught Twitter OAuth
- [x] Publish a new talk ( how to dectect duplicates? )
- [x] Comments by disqus
- [x] Activity list
- [x] Private settings for registered users
- [x] Public profile for registered users
- [x] Public Profile : Published talks list
- [x] Public Profile : Upvoted talks list
- [x] Public Profile : Favorited talks list
- [x] Corporate pages like About, Terms, Policty, FAQ etc ...
- [ ] 100 talks published
- [x] Paginate popular talks
- [x] Paginate latest talks
- [ ] Paginate published talks on profile
- [ ] Paginate upvoted talks on profile
- [ ] Paginate favorited talks on profile

### 0.2.0

We finished our MVP. Now it is time to work on SEO and basic metrics.

Finally as a new features we will introduce following and followers to our
users.

- [ ] SEO ( Jose is your turn, document before start working! )
    - [ ] Start subproject documentation section
    - [ ] Create subproject's roadmap
    - [ ] Create subproject's technical documentation
    - [ ] Write subproject requirements, deployment and developer guidelines
    - [ ] Specify all amount of work needed only based on the current platform
    - [ ] Do not think on future tasks. SEO will always be revisited
- [ ] Add developer environment on chef deployment scripts
- [ ] Add hashbag with a single configuration on chef
    - [ ] On developer environments
    - [ ] On production environments
- [ ] Encrypt hashbag configuration and add this encrypted file to github
    - [ ] using each developer ssh-key? coool!
    - [ ] or a single one? meh ... :\
- [ ] Generate deployed projects configuration with chef
    - [ ] use previous hashbag file.
- [ ] Populate database with chef
    - [ ] On developer environments
    - [ ] Using *db* project backup
    - [ ] Get database configuration from the encrypted hasbag
- [ ] Popuplate index using chef
    - [ ] On developer environments
    - [ ] Using previously populated database
    - [ ] Get index configuration from the encrypted hasbag
- [ ] Minimize all javascript scripts used on production automatically.
- [ ] Add support for javascript source maps for development.
- [ ] Karma : Algorithmic popularity calculation ( docs! subproject? )
- [ ] Sort popular talks by its karma
- [ ] Support Vimeo videos
- [ ] Watch later?
- [ ] Paginate watch later on profile?
- [ ] Mark/Show already watched talks on results?
- [ ] Paginate already watched on profile?
- [ ] Fetch extra information from the user (twitter api? discuss it)
- [ ] Fetch extra information from the talk (youtube api? discuss it)
- [ ] Add slides external link to a talk (optional? discuss it)
- [ ] Metadata! (google search? discuss it)
- [ ] Microformats! (check http://microformats.org )
- [ ] Users: Following / Followers
- [ ] Public Profile: Following users list
- [ ] Paginate following users on profile
- [ ] Public Profile: Followers users list
- [ ] Paginate follower users on profile
- [ ] Modify the youtube player for adding features like "whach it later", can we do that?
- [ ] Show publisher of the talk and its publication date
- [ ] Clicking play on youtube player should increase views on the talk
- [ ] Show upvoters on detailed talk view 

### 0.3.0

Microservices! Microservices!

This is mostly work on Shiva subproject and refactoring the current platform
in favor on a distributed & microservices based architecture.

Another important part to work on this milestone is on the caché, we must
caché everything we can. We need our MVP as fast as hell!

- [ ] Revisit SEO
    - [ ] SEO for profile followers
    - [ ] SEO for profile following
- [ ] Document the architecture of our distributed system.
- [ ] Implement 0.1 version of tlks.io distributed system.
    - [ ] Message bus
    - [ ] Event Manager
    - [ ] Event Scheduler
    - [ ] Queue System
- [ ] Indexing Microservice
    - [ ] Define events
    - [ ] Define payloads
    - [ ] Create producer?
    - [ ] Create consumer that index new published talks on elasticsearch
- [ ] Promotion Microservice
    - [ ] Define events
    - [ ] Define payloads
    - [ ] Create consumer that promotes new talks on Twitter
    - [ ] Create consumer that promotes new talks on Facebook
    - [ ] Create consumer that promotes new talks on Google+
    - [ ] Create consumer that promotes new talks on Pinterest
- [ ] Notification Microservice
    - [ ] Define events
    - [ ] Define payloads
    - [ ] Which consumers we need?
- [ ] Caché everything! ( We should discuss a lot this one, subproject? )
    - [ ] Varnish? NO! big and too easy :\
    - [ ] Redis?
    - [ ] Elastic?
    - [ ] MongoDB?
    - [ ] Multi-Level custom caché? ( I vote for this one ) YES!

### 0.4.0

Enough rock for now, lets make this MVP as solid as Metal. \m/

We will ensure that we have a proper test environment and we will build basic
tests for UNit, Integration and End to End layers. We will also execute those
tests periodically on each component throught *TravisCI* and *coveralls.io*.

As a new feature we will intrdocuce collections of talks to our users.

- [ ] Collections of talks per user ( see collections at producthunt.com )
- [ ] Add a talk to a collection from the detailed view
- [ ] Add a talk to a collection from any list view
- [ ] Public Profile: Collections list
- [ ] Proper Unit Testing suite.
- [ ] Proper End to End Testing suite.
- [ ] Front-end tests via phantomjs.
- [ ] Everything on a CI, in our case *TravisCI*
- [ ] Public code coverage reports using *coveralls.io*
- [ ] Public search documentation syntax ( section help? )
- [ ] Enhaced search query : AND operator
- [ ] Enhaced search query : OR operator
- [ ] Enhaced search query : Wildcard operator
- [ ] Enhaced search query : Phrase search
- [ ] Enhaced search query : Word filters with '-' and '+' modifiers

### 0.5.0

Feedback, Notifications & Devop time!

TODO: This should be discussed!

- [ ] Email notifications to users.
    - [ ] Sendgrid?
    - [ ] How to trigger? Queues again?
- [ ] Just repeat 0.3.0 but for this new microservices arquitecture.
- [ ] Rethink deploy system.
    - [ ] Still with Chef? (I like it)
    - [ ] Docker? ( Our hosting doesn't support it, change to DigitalOcean? )

### 0.6.0

It starts to look as a platform! Now time to think a little bit more,
make this project reliable:

TODO: This should be discussed!

- [ ] Rethink storage
  At this point using a free MongoDB service could not be enough.
- [ ] Rethink search
  Same than above, we are using a free bonsai.io instance.
- [ ] Benchmarks and usage metrics.
    - [ ] How many users we can support with the current resources?
    - [ ] How much will cost to escalate it?
    - [ ] Risks?

### 0.7.0

Ok we have a rock solid platform. Make it pretty, bitch!! :*

TODO: This should be discussed!

- [ ] New logo
- [ ] New layout & design
- [ ] Responsive! At least Desktop, Tablet and High End phones.

### 0.8.0

TODO: This should be discussed!

- [ ] Just repeat 0.3.0 but for this new layout & design.
- [ ] Rethink client-side.
    - Continue with Jade & JQuery? ( probably )
    - [ ] React?
    - [ ] AngularJS?
- [ ] Benchmarks and usage metrics on the client side.
     - [ ] How many users we can support with the current resources?
     - [ ] How muh will cost to escalate it?
     - [ ] Risks?

### 0.9.0

TODO: This should be discussed!

- [ ] Featured collections
- [ ] Public detailed view for user collections
- [ ] Landing page / detailed view for featured collections
- [ ] SEO for Landing feature collection pages
    - [ ] Subdomain? http://pr0n.tlks.io (don't like it)
    - [ ] Canonical? http://tlks.io/pr0n-talks ( yes! yes! )
- [ ] Tune, tweak the platform and prepare the 1.0 version
