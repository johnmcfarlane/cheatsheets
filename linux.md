# Linux

On the desktop I'm most familiar with Debian and its variants, esp. Raspbian and Ubuntu. If you lean towards Redhat or elsewhere, YMMV.

## `sudo`

1. Choose an [editor](editor.md).
1. `su`  
1. `apt-get install sudo`  
1. `visudo`

Then add line

```sh
engelberthumperdinck ALL=(ALL) ALL
```

assuming, of course, that your username is *engelberthumperdinck*. Then quit the editor. (Good luck with that.)

$ `exit`

## `du`

To list **d**isk **u**sage of everything in the current directory in descending order of how badly you want to delete it:

```sh
du --max-depth 1 -ak | sort -rh
```
