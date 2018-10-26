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

#### Prerequisites

--> Install Boost vers 1.59 (ensuring you download the installer for MSVC 14) : https://sourceforge.net/projects/boost/files/boost-binaries/1.59.0/boost_1_59_0-msvc-14.0-64.exe/download (Don't use last versions as 1.68 as it is buggy !)

--> Get cmake 2.8.6 or later : https://cmake.org/files/v3.12/cmake-3.12.3-win64-x64.msi

--> Install Visual Studio 2017 Community Edition : https://visualstudio.microsoft.com/fr/thank-you-downloading-visual-studio/?sku=Community&rel=15#

When installing Visual Studio, it is required that you install following features :

- Desktop development with C++

- VC++ v140 toolchain

The option to install the v140 toolchain can be found by expanding the "Desktop development with C++" node on the right.
You will need this for the project to build correctly (In past versions, this item was called something like VC++ 2015.3 v14.00 (v140) toolset for desktop)

#### Building

##### 1rst part : your_coin.sln generation

--> download your_coin code and unzip it

--> Open files explorer, go to your_coin folder

--> create a new folder called "build" (\your_coin\build)

--> Open Visual Studio 2017 command prompt (you should create a .bat file to open it easilly with : `%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

--> `cd C:\..\your_coin\build`

--> run cmake with BOOST_ROOT option : `cmake -G "Visual Studio 14 Win64" .. -DBOOST_ROOT=C:/local/boost_1_59_0`
You should have generated a "your_coin.sln" file.

##### 2nd part : build

Open the your_coin.sln file with Visual Studio 2017.

In VS Solution Explorer (right pane) right-click **EVERY ITEMS** and select : `Properies -> C/C++ -> Code Generation -> Runtime Library - > change it to Multi-threaded (/MT)`

Verify you have selected Release (and not Debug) and x64

And Finaly do the Build with F5 key.

If all went well..., you should find your .exe file(s) in your_coins/build/src/Release

#### HOW TO RESTORE A WALLET FROM OFFLINE PAPER-WALLET WITH MNEMONIC SEED ?
you need your Mnemonic seed. Don't forget to copy it when creating your wallet. You should copy all the "Private keys" too (spend key + view key)

Then run :

`./simplewallet --restore-deterministic-wallet --wallet-file YOUR_WALLET_NAME`

Enter a password

Enter your mnemonic seed

... and it should work !
