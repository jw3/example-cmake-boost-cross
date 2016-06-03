Example CMake Cross Compile Linux-to-Windows with Boost
-

On Ubuntu 14.04

#####First, install MinGW for cross compiling
- `apt-get install mingw-w64`

#####Then add boost to MinGW
- Credit to http://dev.pawelsz.eu/2013/12/cross-compiling-from-linux-x64-to.html
  - I used Boost 1.61.0
- download and extract the boost dist
- `cp tools/build/example/user-config.jam $HOME`
- `echo "using gcc : 4.8.2 : i686-w64-mingw32-g++ ;" >> $HOME/user-config.jam`
- Configure and prepare build:
    ```
    ./bootstrap.sh mingw \
        toolset=gcc-mingw \
        target-os=windows \
        address-model=32 \
        link=shared,static \
        threading=multi \
        threadapi=win32 \
        --prefix=/usr/i686-w64-mingw32
    ```
- Build and install
    ```
    ./b2 install \
        toolset=gcc-mingw \
        target-os=windows \
        address-model=32 \
        link=shared,static \
        threading=multi \
        threadapi=win32 \
        --prefix=/usr/i686-w64-mingw32 \
        --layout=system release
    ```


At this point you should have a functional cross-compile environment with Boost support.