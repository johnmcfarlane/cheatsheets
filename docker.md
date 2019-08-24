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

Delete all unused volumes:

    docker volume prune

## Lets Make an Ubuntu 16.04 Dev Environment!

1. Get [it](https://hub.docker.com/_/ubuntu) from [Docker Hub](https://www.docker.com/products/docker-hub):

   ```sh
   sudo docker pull ubuntu:16.04
   ```

1. Run it and dive in ([source](https://dockercheatsheet.painlessdocker.com/)):

   ```sh
   sudo docker run -it --name my_container -d ubuntu:16.04
   sudo docker start my_container
   sudo docker attach my_container
   ```

1. Install all the things you _obviously_ need:

   ```sh
   apt update
   apt upgrade
   apt install bash-completion ccache cmake git htop man nano tmux
   ```

1. Fix bash completion ([source](https://askubuntu.com/a/203013/112190), [source](https://askubuntu.com/a/1026978/112190)):

   ```sh
   cp /etc/skel/.bashrc ~/
   rm /etc/apt/apt.conf.d/docker-clean
   ```
   
1. Fixing broken *tmux* default:

   ```sh
   echo "set -g terminal-overrides 'xterm*:smcup@:rmcup@'" >> ~/.tmux.conf
   ```
