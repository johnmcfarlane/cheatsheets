# Secure Sockets Layer

Logging into a remote ssh server at *ssh.deathstar.gov* as *darth*:

$ `ssh darth@deathstar.gov`

Quit a frozen ssh session by pressing the *Return* key followed by:

$ `~.`

Copying a file *from* a remote server to the current directory:

$ `scp darth@deathstar.gov:/Users/darth/Documents/plans.txt .`

Copying a file *to* a remote server to the current directory:

$ `scp ~/Videos/helpme.webm leia@192.168.1.77:/home/r2d2/Desktop`

## SSH Keys

### Introduction

Keys come in pairs:

* a *private* key which use keep secret on your client machine, e.g. *rebellion* and
* a *public* key which is stored on a server, e.g. *rebellion.pub*.

### Creation

[How to create an SSH key](https://help.github.com/articles/generating-ssh-keys/)

### Using the Public Key

### Using the Private Key

Starting *ssh-agent* in your terminal makes it easier to use the keys you've created. In Debian/Ubuntu, add this line to your *~/.bashrc* file:

    eval "$(ssh-agent -s)"

Then before you access the remote service that is using *rebellion.pub*, add your private key to *ssh-agent*:

$ `ssh-add ~/.ssh/rebellion`
