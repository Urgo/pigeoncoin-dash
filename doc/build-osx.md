Mac OS X Build Instructions and Notes
====================================
The commands in this guide should be executed in a Terminal application.
The built-in one is located in `/Applications/Utilities/Terminal.app`.

Preparation
-----------
Install the OS X command line tools:

`xcode-select --install`

When the popup appears, click `Install`.

Then install [Homebrew](https://brew.sh).

Base build dependencies
-----------------------

```bash
brew install automake libtool pkg-config
```

If you want to build the disk image with `make deploy` (.dmg / optional), you need RSVG
```bash
brew install librsvg
```

Building
--------

Follow the instructions in [build-generic](build-generic.md)

Running
-------

Pigeon Core is now available at `./src/pigeond`

Before running, it's recommended you create an RPC configuration file.

    echo -e "rpcuser=pigeonrpc\nrpcpassword=$(xxd -l 16 -p /dev/urandom)" > "/Users/${USER}/Library/Application Support/PigeonCore/pigeon.conf"

    chmod 600 "/Users/${USER}/Library/Application Support/PigeonCore/pigeon.conf"

The first time you run pigeond, it will start downloading the blockchain. This process could take several hours.

You can monitor the download process by looking at the debug.log file:

    tail -f $HOME/Library/Application\ Support/PigeonCore/debug.log

Other commands:
-------

    ./src/pigeond -daemon # Starts the pigeon daemon.
    ./src/pigeon-cli --help # Outputs a list of command-line options.
    ./src/pigeon-cli help # Outputs a list of RPC commands when the daemon is running.
