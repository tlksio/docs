# docs : Developer's Installation

1. [Requirements](devinstall.md#requirements)
2. [Stype by Step installation guide](devinstall.md#requirements)

## Requirements

tlks.io is still in heavy development phase so we mostly use external ( and free ) services to host the project. Once the project reaches its first stable version we will consider final thirth party service we will use.

For now anyway we use **MongoDB** as a database, **Elastic Search** for indexing & search engine and **Twitter OAuth** integration for users.

##### Database

* You should have a database at http://mongolab.com

##### Search

* You should have an elastic search instance at http://bonsai.io

##### Auth & Twitter integration

* You should have a Key and Secret key from http://apps.twitter.com

## Step by Step installation guide


### Vagrant

Install *vagrant* as described at http://www.vagrantup.com/downloads and:

Add an ubuntu server base box to your vagrant environment:

```
$ vagrant box add ubuntu/trusty64
```

### Boot your own VM

First clone the *vagrant* project repository from Github:

```
$ git clone https://github.com/tlksio/vagrant
```

And then boot up the VM:

```
$ vagrant up
```

The result is an Ubuntu Server Box configured as this:

* *IP:* 192.168.33.10
* *Domain:* talks.dev

##### How to connect to this box?

You can connect through ssh to is public IP or domain:

```
$ ssh vagrant@tlks.local
```

### Deploy tlks.io

Now clone  the *chef* project repository from Github:

```
$ git clone https://github.com/tlksio/chef
```

And deploy:

```
$ ./deploy vagrant@tlks.local # Password is 'vagrant'
```

That should take a while, go make a coffee ;)

### Configuration

Now clone the *front* project repository from Github:

```
$ git clone https://github.com/tlksio/chef
```

And based on *configuration.json.dist* create your own *config.json* file.

Example configuration file:

```
{
    "port": 80,
    "twitter_callback_url": "http://tlks.local/auth/twitter/callback",
    "mongodb": "mongodb://xxx:xxx@xxx.dmongolab.com:43180/tlksio",
    "elasticsearch": "https://xxx:xxx@xxx.bonsai.io",
    "twitterConsumerKey": "xxx",
    "twitterConsumerSecret": "xxx"
}
```

Copy the final *config.json* file to your VM:

```
$ scp config.json vagrant@tlks.local:/opt/tlksio/front/config.json
```

Restart:

```
$ vagrant ssh -c "service supervisord restart"
```


Done!

Point your browser to http://tlks.local and happy hacking!


