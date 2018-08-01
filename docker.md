# Docker Containerization

These instructions are incomplete and only tested on Ubuntu 18.04 which is still quite new at time of writing.

## Setup

1. Install docker:

       sudo apt-get install docker

2. Configure and restart:

       sudo systemctl restart docker
       sudo systemctl daemon-reload
       sudo docker run hello-world

## Hacks

### Remove all images and containers

From [TechOverflow](https://techoverflow.net/2013/10/22/docker-remove-all-images-and-containers/):

Delete all containers:

    docker rm $(docker ps -a -q)
    
Delete all images:

    docker rmi $(docker images -q)
