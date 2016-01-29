# Secure Sockets Layer

## Accessing Remote SSH Server

Logging into a remote ssh server at *deathstar.gov* as *darth*:

$ `ssh darth@deathstar.gov`

Quit a frozen ssh session by pressing the *Return* key followed by:

$ `~.`

Copying a file *from* a remote server *to* the current directory:

$ `scp darth@deathstar.gov:/home/darth/Documents/plans.dwg .`

Copying a file *from* the current directory *to* a remote server:

$ `scp plans.dwg darth@deathstar.gov:/home/darth/Documents`

## SSH Keys

### Introduction

Keys come in pairs:

* a *private* key which use keep secret on your client machine, e.g. *empire* and
* a *public* key which is stored on a server, e.g. *empire.pub*.

### Creation

[How to create an SSH key](https://help.github.com/articles/generating-ssh-keys/)

### Uploading the Public Key

To install your public key on a remote server to which you have access:

$ `cat ~/.ssh/empire.pub | ssh darth@deathstar.gov 'cat >> .ssh/authorized_keys'`

You can now log into the remote server without having to type your password:

$ `ssh -i ~/.ssh/empire darth@deathstar.gov`

(Note: some services provide their own way of adding public keys, e.g. [GitHub](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).)

### Adding the Private Key to *~/.gitconfig*

To let *ssh* know that you use private key, *empire*, to access *darth@deathstar.gov*, add the following to a file called *~/.gitconfig*:

    Host crib
      HostName deathstar.gov
      User darth
      IdentityFile ~/.ssh/empire

You can now log into the remote server without having to type your password or specify a key:

$ `ssh darth@deathstar.gov`

### Adding the Private Key to *ssh-agent*

Starting *ssh-agent* in your terminal makes it easier to use the keys you've created. In Debian/Ubuntu, add this line to your *~/.bashrc* file:

    eval "$(ssh-agent -s)"

Then before you access the remote service that is using *empire.pub*, add your private key to *ssh-agent*:

$ `ssh-add ~/.ssh/empire`
