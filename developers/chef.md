# tlks.io : Deploy

This is the chef project documentation. We use this project to deploy a
working version of tlks.io platform to a remote host.

Currently handles:

* OS package updates & ugprades.
* OS depenencies installation.
* Fetching, building and configuring projects source code to
 `/opt/tlks.io` remote folder.
* Restarting the deployed services.

## How to run the deploy?

Execute the following command:

```
$ ./deploy.sh <user@host>
```

Where `<user@host>` is a valid *ssh* login to the server where you want to
deploy *tlks.io*.

## Project structure.

This project consists basically in two *bash* scripts and a list of
*chef-solo* cookbooks to deploy the different components, libraries and
applications that belongs to [lks.io](http://tlks.io).

The two scripts are `deploy.sh` and `install.sh`.

The first script is simple, it wraps a remote ssh command that uploads throught
ssh the project to the remote server. Then executes the next script.

The next script `install.sh` performs the reall deployment on the remote
server. First it checks if chef is installed and if not installs it.
Then executes `chef-solo` to start the cookbooks execution.

#### Chef cookbooks

All chef cookbooks can be found inside the `cookbooks` folder.

Currently we have two active *cookbooks* one that setups the system and
another to deploy the front-end ( currently we only need to deploy this app ).

Check the *chef-solo* documentation to learn how to hack on this cookbooks.
