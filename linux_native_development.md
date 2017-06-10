# Linux Native Development

## GCC From Source

To install GCC in */home/rms/gcc* (user space) on Debian or Ubuntu:

1. Download and unzip, e.g. into */home/rms/Download/gcc*.

2. Install some stuff:

   ```sh
   sudo apt-get install libgmp-dev libmpfr-dev libmpc-dev
   ```

2. Run the `configure` script from a temporary folder:

   ```
   mkdir -p /home/rms/tmp/gcc
   cd /home/rms/tmp/gcc
   /home/rms/Download/gcc/configure --disable-multilib --prefix=/home/rms/gcc/ --enable-languages=c,c++,lto
   ```

3. Build:

   ```
   make -j 8
   ```
       
4. Install:

   ```
   make install
   ```
   
## Alternative Compilers

### Choosing 

To pick between the C++ compilers on a system:

```
sudo update-alternatives --config c++
```

To pick between the GCC compilers on a system:

```
sudo update-alternatives --config g++
```

### Adding

To add new alternative compilers to the list after installing them, e.g. Clang 3.6:

```
sudo update-alternatives --install /usr/bin/cc cc /usr/bin/clang 10
sudo update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++ 10
```

To add new alternative compiler *versions* to the list after installing them:

```
sudo update-alternatives --install /usr/bin/gcc gcc /home/rms/gcc/bin/gcc 10
sudo update-alternatives --install /usr/bin/g++ g++ /home/rms/gcc/bin/g++ 10
```

[[source](http://stackoverflow.com/a/30742451/671509)]

## Binaries

### Inspection

To list libraries linked against an executable or library file, *"my_binary"*:

```
ldd my_binary
```

To list symbols in *.o* file, *"my_object_file.cpp.o"*:

```
nm my_object_file.cpp.o
```

### Debugging

Your program, *my_binary*, crashed and you were promised a *core* file ... but they lied!

1. First, make sure *my_binary* is compiled with [debugging information](https://gcc.gnu.org/onlinedocs/gcc-3.4.5/gcc/Debugging-Options.html).
   Typically this means adding the `-g` flag to your compiler options.

1. Lift the limit on core file size:

   ```
   ulimit -c unlimited
   ```

1. Re-run *my_binary*:

   ```
   ./my_binary
   ```

   and you should find a *core* file in your working directory.

1. Now print the stack:

   ```
   gdb ./DoCoolStuff core -batch -ex bt
   ```
