# Linux Native Development

## GCC From Source

To install GCC 7.2 in */home/rms/gcc-7.2.0* (user space) on Debian or Ubuntu:

1. Clone

   ```sh
   git clone git://gcc.gnu.org/git/gcc.git
   ```

1. Install some stuff:

   a. On Debian or Ubuntu:
   
      ```sh
      sudo apt-get install flex libgmp-dev libmpfr-dev libmpc-dev
      ```
   
   b. On Redhat:
   
      ```sh
      sudo yum install flex gmp-devel mpfr-devel libmpc-devel
      ```

1. Run the `configure` script from a temporary folder:

   ```
   mkdir -p build && cd build
   path-to-gcc/configure --disable-bootstrap --disable-multilib --prefix=/home/rms/gcc-7.2.0/ --enable-languages=c,c++,lto
   ```

5. Build:

   ```
   make -j $(nproc)
   ```
       
6. Install:

   ```
   make install
   ```

## Clang With the Trimmings

1. ```sh
   git clone https://github.com/llvm/llvm-project.git
   ```

2. ```sh
   mkdir build
   cd build
   cmake CXX=clang++ CC=clang cmake ../llvm-project/llvm/ -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_COMPILER_LAUNCHER=ccache -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra;libcxx;libcxxabi;compiler-rt" -DCMAKE_INSTALL_PREFIX=/home/john/llvm -G Ninja
   ```
   
MemorySanitizer is an especially difficult tool to use because it requires the standard library to be built instrumented.
Here's a recipe for configuring all that:

```sh
CXX=clang++ CC=clang cmake ../llvm-project/llvm/ -DCMAKE_BUILD_TYPE=MinSizeRel -DCMAKE_CXX_COMPILER_LAUNCHER=ccache -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra;libcxx;libcxxabi;compiler-rt" -DLLVM_USE_SANITIZER=Memory -DCMAKE_INSTALL_PREFIX=/home/john/llvm -G Ninja
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
sudo update-alternatives --install /usr/bin/gcc gcc /home/rms/gcc-7.2.0/bin/gcc 10
sudo update-alternatives --install /usr/bin/g++ g++ /home/rms/gcc-7.2.0/bin/g++ 10
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

### Demangling

Use [`c++filt`](https://sourceware.org/binutils/docs/binutils/c_002b_002bfilt.html) to demangle C++ symbols. It is a very versatile tool that can be used in any text containing mangled C++, e.g.:

```
perf report | c++filt | less -S
```

### Debugging

Your program, *my_binary*, crashed and you were promised a *core* file ... but they lied!

1. First, make sure *my_binary* is compiled with [debugging information](https://gcc.gnu.org/onlinedocs/gcc-3.4.5/gcc/Debugging-Options.html).
   Typically this means adding the `-g` flag to your compiler options.

1. Lift the limit on core file size:

   ```
   ulimit -c unlimited
   ```

1. Disable Apport:

   ```sh
   sudo systemctl disable apport.service
   ```

1. Edit _core_pattern_

   ```sh
   sudo nano /proc/sys/kernel/core_pattern
   ```
   
   and replace file with "core".

1. Re-run *my_binary*:

   ```
   ./my_binary
   ```

   and you should find a *core* file in your working directory.

1. Now print the stack:

   ```
   gdb ./DoCoolStuff core -batch -ex bt
   ```

### Disassembly

```sh
objdump -d -Mintel <object-file>
```
