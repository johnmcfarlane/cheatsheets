# Docker Containerization

These instructions are incomplete and only tested on Ubuntu 18.04 which is still quite new at time of writing.

## Setup

1. Install docker:

       sudo apt-get install docker

1. Configure and restart:

       sudo systemctl restart docker
       sudo systemctl daemon-reload
       sudo docker run hello-world
       
1. Avoid having to type `sudo` all the time:

   ```sh
   sudo gpasswd -a $USER docker
   newgrp docker
   ```

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
   apt install bash-completion ccache cmake git htop iputils-ping man nano tmux
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

## Better Still, Make a Dockerfile!

1. Populate a Dockerfile like [this one](https://github.com/elcojacobs/brewblox-firmware/blob/ed70d66f0495103663173fbc5f6c9ba532b41817/docker/compiler/Dockerfile) and build it:

   ```sh
   docker build .
   ```

1. Identify the image:

   ```sh
   docker images
   ```
   
   > REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
   > <none>              <none>              019f4128c46e        11 seconds ago      146MB
   > ubuntu              16.04               5e13f8dd4c1a        4 weeks ago         120MB
   
   Hint: it's 019f4128c46e.

1. Create a container

   ```sh
   docker run -it --name my_container -d 019f4128c46e
   ```

1. Dive in!

   ```sh
   docker attach my_container
   ```
