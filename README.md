# docker-laravel

## Prerequisites

This setup assumes you are running Docker on a computer with at least 4GB of allocated RAM, a dual-core, and an SSD hard drive.

This configuration has been tested on Linux. Windows is supported through the use of Docker on WSL

## Basic setup

### Setup new laravel projects
```bash
#bin/setup version base_url
 bin/setup 8.0 myhost.com
```

If you want to change to something else, go and check bin/setup file. The Laravel source code is located at src folder.

### Setup with more option or existing projects 

```bash
bin/setup-project
```

Then the command will prompt you to input some information as below:
- **Git url**: Git url of your exist project or your empty git repository. Ex: *https://github.com/katScript/laravel-docker.git* or *git@github.com:katScript/laravel-docker.git*
- **Branch**: Git branch you want to use. Ex: *main* or *master*
- **Database**: The backup database file. You can download the database, create new ***mysql*** folder and put it there then specify the path as input. Ex: mysql/fileName.sql
- **ENV File**: Because we will not run the setup from the beginning, we need to provide the .env file. Prepare the file then specify the path as input. Ex: env/.env
- **Base Url**: The base url you want to use on your local. The command will help to input to hosts file and setup the ssl self-certificate. Ex: myhost.com

## Usefull commands

There are lots of commands you can use in bin folder.
- `bin/status`: Check the status of all containers.
- `bin/start`: Start the containers.
- `bin/stop`: Stop the containers.
- `bin/restart`: Restart the containers.
- `bin/removeall`: Remove all docker related things: container, networks, volumes and images.
- `bin/composer`: Run the composer binary. Ex: `bin/composer update`.
- `bin/artisan`: Run the Laravel CLI. Ex: `bin/artisan migrate`.
- `bin/mysql`: Access to mysql container.
- `bin/mysql-export`: Export database.
- `bin/mysql-import`: Import database.
- `bin/bash`: Drop into the bash prompt of your phpfpm Docker container. The `phpfpm` container should be mainly used to access the filesystem within Docker.
- `bin/cli`: Run any CLI command without going into the bash prompt. Ex. `bin/cli ls`.
- `bin/clinotty`: Run any CLI command with no TTY. Ex: `bin/clinotty chmod u+x artisan`.
- `bin/fixowns`: This will fix filesystem ownerships within the container.
- `bin/fixperms`: This will fix filesystem permissions within the container.

### Redis

Redis is now the default cache and session storage engine, and is automatically configured & enabled when running `bin/setup` on new installs.

### Linux

Running Docker on Linux should be pretty straight-forward. Note that you need to run some [***Post install commands***](https://docs.docker.com/install/linux/linux-postinstall/) as well as [***installing Docker Compose***](https://docs.docker.com/compose/install). These steps are taken care of automatically with Docker Desktop, but not on Linux.