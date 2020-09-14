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

## Difficult X11 Servers

Some things to try:

1. Add these to _/etc/ssh/sshd_config_:

   ```
   X11Forwarding yes
   X11DisplayOffset 10
   X11UseLocalhost yes
   ```

2. Run `xauth`:

   ```bash
   xauth add localhost/unix:10 MIT-MAGIC-COOKIE-1 d65608ea2a561b4ec6cf137e0e99f635
   ```
 
3. Use `gnome-terminal.real` instead of `gnome-terminal`.

## One-liners

### `du`

To list **d**isk **u**sage of everything in the current directory in descending order of how badly you want to delete it:

```sh
du --max-depth 1 -ak | sort -rh
```

### Cheap WinDirStat:

All the files/directories in your home directory, biggest first:

```sh
du -ah --max-depth 1 ~ 2> /dev/null | sort -hr | less
```

### Newest Files

All the files in your home directory, newest first:

```sh
find ~ -type f | xargs stat -c "%y %n" 2> /dev/null | sort -r | less
```
