DEPRECATED

No longer maintained in favor of https://github.com/NodeBB/docker-builds
Node.js Dockerfile

This repository contains the Dockerfile of NodeBB for Docker's automated build published to the public Docker Hub Registry.
Base Docker Image

    dockerfile/redis

Requirements

    Docker

Usage

First, run a Redis instance on your machine. It will automatically expose the /data volume.

docker run --name my-forum-redis -d dockerfile/redis

Next, launch the NodeBB instance from this repository, so it links with the just-launched Redis instance.

docker run --name my-forum-nodebb --link my-forum-redis:redis -P -t -i nickjanssen/nodebb

You will be asked to configure your NodeBB instance, as no config file was found. Simply press enter for all settings except Redis hostname, which should be redis as it is linked using the --linked parameter to our Redis instance, and the administrator username, e-mail and password.

NodeBB will launch the setup and automatically close. Next, simply start the instance again. It will this time find a config file and start as a daemon.

docker start my-forum-nodebb

Your NodeBB instance will be accessible on port 4567. Check docker ps for more details.
Backup/Restoring

Simply use the /data volume inside your Redis instance. See the official guide on making backups.
