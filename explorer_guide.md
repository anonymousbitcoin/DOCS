# How to run the ANON Explorer

In this guide, we will go over how to set up the Block Explorer on a VPS.

This guide is intended for advanced users who wish to help support the community, or who require a personal block explorer for their own needs.

## Installation

Assuming you are on a fresh Linux droplet, install dependencies.

The dependencies required are: `git, zmq, libtool, pkg-config, build-essential, autoconf, and automake`. These dependencies can be installed with the following command:

```
sudo apt-get install git && libtool && pkg-config && build-essential && autoconf && automake
```

For `zmq`:

```bash
git clone https://github.com/zeromq/libzmq
cd libzmq
mkdir cmake-build && cd cmake-build
cmake .. && make -j 4
make test && make install && sudo ldconfig
```

Next, we need to ensure we have node fully installed.

```bash
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install nodejs npm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
export NVM_DIR="${XDG_CONFIG_HOME/:-$HOME/.}nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

**IMPORTANT:** After installation, switch to node version 8.0.0:

```bash
nvm install 8.0.0
```

If you have any installation issues, refer to [this link](https://gist.github.com/d2s/372b5943bce17b964a79) for further documented support on `nvm`.

Next, we need to clone the `bitcore-node-anon` repository found [here](https://github.com/anonymousbitcoin/bitcore-node-anon).

<!-- MOVE THE ADDITIONAL STUFF TO THE BOTTOM -->

```bash
# outside of libzmq
cd ~

# clone bitcore-node-anon
git clone https://github.com/anonymousbitcoin/bitcore-node-anon.git

cd bitcore-node-anon

# install node modules
sudo npm i

# symlink anond into the bin folder
ln -s ~/path/to/anon/src/anond ./bin/anond

# create the explorer
./bin/bitcore-node create <name_of_node>

cd <name_of_node>
```

Using Vim or Nano, modify the `bitcore-node.json` file so that the `servicesConfig` mirrors the following:

```json
"servicesConfig": {
    "bitcoind": {
      "spawn": {
        "datadir": "/root/.anon/",
        "exec": "/root/path/to/bitcore-node-anon/bin/anond"
      }
    }
  }
```

Next, within the `<name_of_node>` directory, run the following command to install the `insight-api-anon` and `insight-ui-anon` that the front end will require.

```bash
../bin/bitcore-node install anonymousbitcoin/insight-api-anon anonymousbitcoin/insight-ui-anon
```

Afterwards, edit the `anon.conf` file within your chosen data directory.

```vim
debug=1
showmetrics=0
txindex=1
rpcport=3005
server=1
whitelist=127.0.0.1
addressindex=1
timestampindex=1
spentindex=1
rpcallowip=127.0.0.1
rpcuser=bitcoin
rpcpassword=local321
uacomment=bitcore
zmqpubrawtx=tcp://127.0.0.1:28332
zmqpubhashblock=tcp://127.0.0.1:28332
```

Once thats all completed, you are ready to start the bitcore node with the following command:

```bash
# from within the <name_of_node> directory
../bin/bitcore-node start
```

### Advanced modifications

Should you wish to make any modifications to the libraries, you would have to `git clone` those libraries and symlink them into the `node_modules` folder of the `bitcore-node-anon` as well as any library that uses that library. Further documentation can be found on the [bitcore homepage](https://bitcore.io/)

