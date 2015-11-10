# Linux Native Development

## Alternative Compilers

### Choosing 

To pick between the C++ compilers on a system:

$ `sudo update-alternatives --config c++`

## Adding

To add new alternative to the list after installing them, e.g. Clang 3.6:

$ `sudo update-alternatives --install /usr/bin/cc cc /usr/bin/clang-3.6 100`
$ `sudo update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++-3.6 100`

[[source](http://stackoverflow.com/a/30742451/671509)]

## Binaries

$ `lld my_binary` - list libraries linked against an executable or library
