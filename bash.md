# Bash

BASH is an acronym of Bourne Again SHell.

## Initial Script

On most Linux variants, the file, *.bashrc*, located in your home directory contains commands that are run when you start a terminal:

$ `editor ~/.bashrc`

([more about the editor](editor.md))

### Things to Add to *.bashrc*

To add a directory a the list of paths search for binaries:

    export PATH=$PATH:/home/luke/bin

To start the *ssh-agent*:

    eval "$(ssh-agent -s)"

([more about ssl](ssl.md))
