## Standard Hub toolchains

armv7l-linux-musleabihf-cross toolchains for Linux build host PC (x64)

This toolchain can be used to build for the development container that we run on the Standard Hub.

## Usage

- Untar into a folder of your choosing on your Linux x64 build host PC. 
- Integrate using CMake (toolchain file) or GNU Make (manually)

### Note on sysroot synchronization

When you add packages to the alpine-dev `Dockerfile`, you need to ensure that you sync your sysroot.
This means that the following should be "rsync" or copied from the alpine-dev container to your toolchain sysroot:

- /usr/include/*.h
- /usr/lib/*.so
- /usr/lib/*.a
- /lib/*.so
- /lib/*.a

This will allow the cross compilation on your build host to include headers and link against libraries that are installed as a result of including extra packages (e.g. mosquitto-dev, openssl-dev)
