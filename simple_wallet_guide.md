# Wallet Guide for Beginners

This guide assumes that you have already installed the [ANON Full Node](https://github.com/anonymousbitcoin/anon), and followed [this guide](https://gist.github.com/kaypon/4e6863e26f21fca9f5b8b350350912a1).

To install the wallet, you'll need to download the source code from the [ANON Github](https://github.com/anonymousbitcoin/anon-full-node-wallet). It is important that you followed the above mentioned guide, as the wallet will need to be built in the `/src/` folder where installed ANON previously.

## Install the wallet (MAC)

In your terminal copy and enter the following:

```
# You need to know where you copied ANON full node.

cd ~/path/to/anon/

cd /src/

git clone https://github.com/anonymousbitcoin/anon-full-node-wallet.git

cd anon-full-node-wallet

./gradlew clean fatjar

cd build/libs

chmod u+x AnonymousDesktopWallet-1.1.0.jar
```

At this point, you have built and compiled the wallet. There are two options on how to start it. The first, through the terminal simply type:

```
java -jar AnonymousDesktopWallet-1.1.0.jar
```

Or, alternatively you can open the directory in finder using the command:

```
open .
```

This will open a finder window, and you can simply double click the `AnonymousDesktopWallet-1.1.0.jar` executable. 

## Install the wallet (LINUX)

```
# You need to know where you copied ANON full node.

cd ~/path/to/anon/

cd /src/

git clone https://github.com/anonymousbitcoin/anon-full-node-wallet.git

cd anon-full-node-wallet

./gradlew clean fatjar

cd build/libs

chmod u+x AnonymousDesktopWallet-1.1.0.jar
```
