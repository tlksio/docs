# docs : Developer's Installation

1. [Requirements](devinstall.md#requirements)
2. [Database creation](devinstall.md#database_creation)
3. [Full-Text index creation](devinstall.md#full-text_index_creation)
2. [Stype by Step deploy guide](devinstall.md#step-by-step-installation-guide)
	1. [Vagrant](devinstall.md#vagrant)
	2. [Create a Virtual Machine](devinstall.md#create_a_virtual_machine)
	3. [Deployment script](devinstall.md#deploy_tlks_io)
	4. [Configuration](devinstall.md#configuration)
	5. [Start & Stop services](devinstall.md#start_stop_services)

## Requirements

[tlks.io](http://tlks.io) is still in heavy development phase!!

And this is the main reason that currently we only use external ( and free )
thirth party services on the project. Once the project reaches its first stable
version we will consider final thirth party or custom service we will use for
each component.

Anyway, this are the main dependencies we currently have:

We are using **MongoDB** as a database and it is located at
http://mongolab.com so please create your own account there in case you want
to hack on tlks.io.

Our full-text index and search egine is **Elastic Search**, the index is
located at http://bonsai.io so you will also need to create an account there.

Finally we delegate the authorization of our users to *Twitter* using its
**Twitter OAuth** service. You will need to create an app called for example
*tlks.local* at http://apps.twitter.com. This application will be used
to make *OAuth* calls using its *ConsumerKey* and *ConsumerSecret* keys
provided.

## Database creation

Our provider of choice for *MongoDB* right now is http://mongolab.com. You
should create an user at mongolab.com.

Refer to [MongoLab's documentation](http://docs.mongolab.com/) for more
information.

##### Create the database

Create a database called `tlksio`. You should also create an user and set up
the password on this database.

Later you will need the connection string to this database wich is something
like this:

`mongodb://XXXXX:XXXX@XXXXXXXX.mongolab.com:XXXXX/tlksio`

##### Database backup / import

We have a project called **db** at https://github.com/tlksio/db for this:

It saves all documents stored on MongoDB to json files. Those files are also
commited to Github to have something to work with ;)

* `node ./backup.js` to backup the database.
* `node ./import.js` to import the database.
   ( in progress!  TODO: link to an issue)

## Full-Text index creation

In the same way than for the database we use an external service for searching
and indexing. Our choice in this case is http://bonsai.io. You need an user
there too.

##### Create an index

Create an index with your user at http://bonsai.io.

##### Indexing the database.

Note that you need a database created with data imported before building the
index!

We have a project called **cli** at https://github.com/tlksio/cli ( that
should be our main cli tool to manage the platform but this is another topic )
used to rebuild the index from scratch.

To install this tool:

```
$ git clone https://github.com/tlksio/cli
$ cd cli
$ npm install
```

To reindex the database:

```
$ node . --reindex
```

##### Auth & Twitter integration

We don't handle the authentication of users at http://tlks.io, we delegate all
this feature to *Twitter* and we use *Twitter OAuth*.

Create an app at https://apps.twitter.com and get its *ConsumerKey* and
*ConsumerSecret* values.

## Step by Step deploy guide

### Vagrant

Install *vagrant* as described at http://www.vagrantup.com/downloads and
add an *ubuntu server* base box to your *vagrant* environment:

We use *Ubuntu* 14.04 64 bits as a base *OS*.

```
$ vagrant box add ubuntu/trusty64
```

### Create a Virtual Machine

First clone the *vagrant* project repository from Github:

```
$ git clone https://github.com/tlksio/vagrant
```

And then boot up the VM:

```
$ vagrant up
```

Finally provision the VM, it upgrades the system and install
global dependencies:

```
$ vagrant provision
```


##### VM Information

The result is an *Ubuntu Server Box* configured as this:

* **IP:** 192.168.33.10
* **Domain:** tlks.local
* **Users:** It has 2 users, *vagrant* and *toot* both with `vagrant` password.
* **DNS:** *avahi-daemon* is installed, so the box resolves as `tlks.local` to
  the internal network.

##### Test if your new VM is up and running!

From outside the VM, inside the local network:

```
$ ping tlks.local
PING tlks.local (192.168.33.10) 56(84) bytes of data.
64 bytes from tlks.local (192.168.33.10): icmp_req=1 ttl=64 time=0.657 ms
64 bytes from tlks.local (192.168.33.10): icmp_req=2 ttl=64 time=0.635 ms
64 bytes from tlks.local (192.168.33.10): icmp_req=3 ttl=64 time=0.653 ms
64 bytes from tlks.local (192.168.33.10): icmp_req=4 ttl=64 time=0.551 ms
c64 bytes from tlks.local (192.168.33.10): icmp_req=5 ttl=64 time=0.570 ms
^C
--- tlks.local ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.551/0.613/0.657/0.046 ms
```

From inside the VM:

```
$ vagrant ssh -c "dig tlks.local"
;; Warning: Message parser reports malformed message packet.

; <<>> DiG 9.9.5-3ubuntu0.2-Ubuntu <<>> tlks.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12918
;; flags: qr aa rd ra ad; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;tlks.local.                    IN      A

;; ANSWER SECTION:
tlks.local.             3600    IN      CNAME   tlks.local.
tlks.local.             3600    IN      A       192.168.33.10

;; Query time: 4 msec
;; SERVER: 10.0.2.3#53(10.0.2.3)
;; WHEN: Tue Mar 10 22:59:45 UTC 2015
;; MSG SIZE  rcvd: 68

Connection to 127.0.0.1 closed.
```


#### How to connect to this box?

You can connect through ssh to is public IP or domain:

```
$ ssh vagrant@tlks.local
```

This *vagrant* user is a *sudoer*,and does not need password to execute
privileged commands.

### Deploy tlks.io

Our deployment is based in *chef* and its tool *chef-solo* to handle it.

Refer to the the documentation of *chef-solo* at
https://docs.chef.io/chef_solo.html for more information.

[tlks.io](http://tlks.io) stores all chef *cookbooks* and deploy related
*scripts* in a separate repository project. This project is willing to be
the official and unique way to deploy *tlks.io* both for production than for
development.

Documentation for this project is available in a separated document, please
refer to the [deployment documentation](deploy.md) in case you need it.

To continue clone the *chef* project source code:

```
$ git clone https://github.com/tlksio/chef
```

And just execute the deployment script, followed the host and user where you
want to deploy the platform in a ssh account format.

In case you are using a previously created VM you should execute this command:

```
$ ./deploy vagrant@tlks.local
```

The password for the user *vagrant* is `vagrant` but we recomend that you push
your ssh key to the VM to not worry about it.

That should take a while, go make a coffee ;)

### Configuration

Now clone the *front* project repository from Github. This is the front-end
repository project and currently the only service deployed by the platform.

```
$ git clone https://github.com/tlksio/front
```

You will notice that, there is a `configuration.json.dist` file at the
project's root folder. This is a template configuration tlks.io front-end web
application file.

Copy this tempate to the file used by the application:

```
$ cp config.json.dist config.json
```

Remember all those accounts, database and index that you created at the
beginning of this document? Now is the time to get their settings and build
a custom configuration file.

Complete the configuration json file as described with you own information.

Example configuration file:

```js
{
    // Port where the app should bind.
	// If you are deploying to a VM, just use port 80.
	"port": 80,

 	// Twitter OAuth authorization callback url.
    // If you are deploytin to a VM, you don't need to change it.
    "twitter_callback_url": "http://tlks.local/auth/twitter/callback",

	// MongoDB connection string.
	"mongodb": "mongodb://xxx:xxx@xxx.dmongolab.com:43180/tlksio",

	// Elastic Search connectino string.
	"elasticsearch": "https://xxx:xxx@xxx.bonsai.io",

    // Twitter APP keys
  	"twitterConsumerKey": "xxx",
    "twitterConsumerSecret": "xxx"
}
```

Copy the final *config.json* file to your VM:

```
$ scp config.json vagrant@tlks.local:/opt/tlksio/front/config.jso<n
```

Notice that you need to rip off all the comments before, *JSON* doen't support
them!

### Start and Stop services

To restart just send a command via vagrant and ssh to restart the *supervisord*
instance on the VM.

```
$ vagrant ssh -c "service supervisord restart"
```


Done!

Point your browser to http://tlks.local and happy hacking!
