# Linux Native Development

## Alternative Compilers

### Choosing 

To pick between the C++ compilers on a system:

$ `sudo update-alternatives --config c++`

### Adding

To add new alternative to the list after installing them, e.g. Clang 3.6:

$ `sudo update-alternatives --install /usr/bin/cc cc /usr/bin/clang-3.6 100`

$ `sudo update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++-3.6 100`

[[source](http://stackoverflow.com/a/30742451/671509)]

## Binaries

### Inspection

To list libraries linked against an executable or library file, *"my_binary"*:

$ `ldd my_binary`

To list symbols in *.o* file, *"my_object_file.cpp.o"*:

$ `nm my_object_file.cpp.o`

### Debugging

Your program, *my_binary*, crashed and you were promised a *core* file ... but they lied!

1. First, make sure *my_binary* is compiled with [debugging information](https://gcc.gnu.org/onlinedocs/gcc-3.4.5/gcc/Debugging-Options.html).
   Typically this means adding the `-g` flag to your compiler options.

1. Lift the limit on core file size:

   $ `ulimit -c unlimited`

1. Re-run *my_binary*:

   $ `./my_binary`

   and you should find a *core* file in your working directory.

1. Now print the stack:

   $ `gdb ./DoCoolStuff core -batch -ex bt`
