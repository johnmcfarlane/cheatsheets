# Linux

On the desktop I'm most familiar with Debian and its variants, esp. Raspbian and Ubuntu. If you lean towards Redhat or elsewhere, YMMV.

## `sudo`

$ `su`  
$ `apt-get install sudo`  
$ `visudo`

Then add line

```sh
engelberthumperdinck ALL=(ALL) ALL
```

assuming, of course, that your username is *engelberthumperdinck*. Then quit the editor. (Good luck with that.)

$ `exit`
