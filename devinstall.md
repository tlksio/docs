# docs : Developer's Installation

## Requirements

Install *vagrant* as described at http://www.vagrantup.com/downloads and:

Add an ubuntu server base box to your vagrant environment:

```
$ vagrant box add ubuntu/trusty64
```

## Boot your own VM

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

### How to connect to this box?

You can connect through ssh to is public IP or domain:

```
$ ssh vagrant@tlks.local
```

## Deploy tlks.io

Now clone  the *chef* project reposotory from Github:

```
$ git clone https://github.com/tlksio/chef
```

And deploy:

```
$ ./deploy vagrant@tlks.local # Password is 'vagrant'
```

Done!

Point your browser to http://tlks.local and happy hacking!

