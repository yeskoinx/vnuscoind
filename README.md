# Elphyrecoin [ELPH]

Website : https://www.elphyrecoin.xyz

## Building ElphyreCoin

### On *nix :

#### To install dependencies on Ubuntu :

If you are using Ubuntu 18.x you may need to downgrade gcc7 to gcc 6. There is an example of how to do so in the scripts/ directory.

**Ubuntu 18.x**
`sudo apt install build-essential cmake libboost-all-dev miniupnpc libunbound-dev graphviz doxygen libunwind8-dev pkg-config libssl-dev libcurl4-openssl-dev libgtest-dev libreadline-dev libminiupnpc-dev libzmq3-dev libsodium-dev libpgm-dev libnorm-dev`

**Ubuntu 16.x**
`sudo apt install build-essential cmake libboost-all-dev miniupnpc libunbound-dev graphviz doxygen libunwind8-dev pkg-config libssl-dev libcurl4-openssl-dev libgtest-dev libreadline-dev libminiupnpc-dev libzmq3-dev libsodium-dev libpgm-dev`

#### Cloning the rep :
`git clone https://github.com/elphyrecoin/elphyrecoin.git`

#### To build :

`cd elphyrecoin`

`make`

The resulting executables can be found in build/release/src.

Advanced options:

Parallel build: run `make -j<number of threads>` instead of `make`... only if you have enough RAM (>= 2 GB)

For example, if you have a CPU with 4 threads, run : `make -j 4`

### On Windows:

Dependencies: MSVC 2013 or later, CMake 2.8.6 or later, and Boost 1.55 or later. You may download them from:

http://www.microsoft.com/

http://www.cmake.org/

http://www.boost.org/

Donwload the last sourcecode (zip file) here : https://github.com/elphyrecoin/elphyrecoin/releases

Open the Windows command line and change to the Elphyrecoin's directory. Then, run this command:

`mkdir build && cd build && cmake .. -G "Visual Studio 15 2017 Win64" ..`

You should have generated a Elphyrecoin.sln file. Then open this File in VisualStudio (2017).

In VisualStudio, in VS Solution Explorer, find `upnpc-static` then :

`right click : Properies -> C/C++ -> Code Generation -> Runtime Library - > change it to Multi-threaded (/MT)`

And Finaly do the Build with F5 key.
