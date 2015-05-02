# tlks.io : Event manager & queue system

This subproject is planed for the future 0.3.0.

You should not be working here, this is only a quick overview document
that will serve as an start-point to I+D and write a proper documentation and
specs for the project.

## Overview

This subproject will handle all pieces of work that can be decoupled from the
different applications that belongs to the front-end subproject. Will allow
to transform tlks.io into a true distributed and microservices based platform
instead of a big & complex monolithic one.

3 different components are going to be provided by its subproject:

### A global message bus

* uses the event manager and the queue system
* handles registration of all active microservices
    * only allow registered microservices to interact with the bus
    * common API for microservices
    * HTTP & REST based protocol
    * documented API specification using API BluePrint
    * unit tested spec ( not code! )
    * defensive programming approach of its development
* handles communication between all microservices
    * common API to publish messages
    * common API to subscribe messages
    * HTTP & REST based
    * publish subscribe pattern implementation ( pubsubhubbub )
    * documented API specification using API BluePrint
    * unit tested spec ( not code! )
    * defensive programming approach of its development
* JSON as a global data transport format for message payloads
* globally handle exceptions and errors on all registered microservices
    * common errors message specification/codification
    * microservices are expected to not break its execution never
* configurable logging system
    * per topic
    * per consumer
    * per producer
* message pre and post process using middleware pattern
    * compress payloads to save space/memory
    * enhance payload with producer authorization
    * message validation?

###### Ideas

* monitor / control its execution in real time (without restart)
* HTTP streaming support message handling
* authorization ( do not use passwords! Use tokens! )?
* support webhooks?
* support socket.io clients?
* support smtp clients?
* support sms clients?
* secure message communication using JSON web tokens
* distributed bus or, multiple buses on different hosts
    * replication
    * sharding

###### Questions

* Is this a server? a web application?
* data structure used to store registered microservices? FAST! SIMPLE!
* Unique id for a registered microservice?
* what is the metadata for a registered microservice?
* data structure to store the message payload request?
* shall we persist message responses?
* data structure to store the message payload response?
* common schema envelope for a message?
* common schema format for an error?
* How we log bus activity?

### A distributed event manager

* implement observer pattern on message bus data structures
* support for synchronous events
    * A triggered event must wait for a response
    * Event is completed when the response is received
    * Producer knows when the message is processed
* support for asynchronous events
    * A trigged event doesn't waits for a response
    * Producer doesn't know when the message is processed
    * A function callback is provided
* support for scheduled events
    * Event triggers on specific moments
    * Support cront-tab like definition format for date triggering
* support for topic based routing : multicast
    * Topics are collections of typed events
    * Topics are implemented using a queue system
    * Topics optionally, can be tunned to support different queue disciplines
    * Producers publish messages to topics
    * Consumers subscribe topics to receive messages
    * Producers can write to one or multiple topics
    * Consumers can subscribe to one or multiple topics

###### Ideas

* support for content based routing
    * middle-ware pattern to pre-process producer messages
    * partial/regexp/jsonpath query engine to match message payloads
    * Producers publish payloads directly without a topic name
    * Each different match query produces a new topic
    * Consumers can subscribe to this automatically topic  

###### Questions

* Is this a library?
* What is an event? Do you have an example?
* How is codified an event? And its payload?
* What happens if a synchronous event fails? Message is discarded?
* Can we assure a message is processed only once? Shall we?
* Can we assure a message is processed at least once? Shall we?
* How we log event activity?
* What is event routing?
* How to check for scheduled events periodically?
* Can be producers also scheduled events?
* Can be consumers also scheduled events?
* What is a Topic?
* What is multicast?
* data structure for the collection of data types is our queue system?

### A multi-queue system

* support for first in first out discipline
* support for last in first out discipline
* support for priority discipline

###### Ideas

* Define a CRUD on steroids as a common API for the persistence API.
* common data persistence interface
    * in memory persistence driver
    * file system persistence driver
    * database persistence driver
        * Redis

###### Questions

* Which data structure is a queue?
* What is first in first out?
* What is last in first out?
* What is a priority discipline?
* Can i use more than an queue at once?
* Can different queues use different disciplines?
* How can we log queue activity?
