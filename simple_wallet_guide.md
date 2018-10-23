# Wallet Guide for Beginners

- [Mac Guide](#mac-guide)
- [Linux Guide](#linux-guide)
- [Windows Guide](#windows-guide)

This guide assumes that you have already installed the [ANON Full Node](https://github.com/anonymousbitcoin/anon), and followed [this guide](https://gist.github.com/kaypon/4e6863e26f21fca9f5b8b350350912a1).

To install the wallet, you'll need to download the source code from the [ANON Github](https://github.com/anonymousbitcoin/anon-full-node-wallet). It is important that you followed the above mentioned guide, as the wallet will need to be built in the `/src/` folder where installed ANON previously.

## Mac Guide

First, ensure you have [JDK10](https://docs.oracle.com/javase/10/install/overview-jdk-10-and-jre-10-installation.htm#JSJIG-GUID-8677A77F-231A-40F7-98B9-1FD0B48C346A) installed.

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

mv AnonymousDesktopWallet-1.1.0.jar ../../../

cd ../../../
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

Alternatively, if you wish to download the latest version, it can be found in the [releases section](https://github.com/anonymousbitcoin/anon-full-node-wallet/releases) of the ANON repo. 

**NOTE:** the file `AnonymousDesktopWallet-1.1.0.jar` **MUST** be placed within the same directory as your `anond` and `anon-cli`. The wallet uses both those compiled binary files to communicate to the blockchain. Without those two files, the wallet **will not** work.

## Linux Guide

Ensure that you have Java's default JDK installed.

```
sudo apt-get install git default-jdk ant
```

Now, you need to find where you installed the ANON full node previously.

```
cd ~/path/to/anon/

cd /src/

git clone https://github.com/anonymousbitcoin/anon-full-node-wallet.git

cd anon-full-node-wallet

./gradlew clean fatjar

cd build/libs

chmod u+x AnonymousDesktopWallet-1.1.0.jar

mv AnonymousDesktopWallet-1.1.0.jar ../../../

cd ../../../
```

At this point, you have built and compiled the wallet. There are two options on how to start it. The first, through the terminal simply type:

```
java -jar AnonymousDesktopWallet-1.1.0.jar
```

Or, alternatively you can open the directory in finder using the command:

```
nautilus .
```

This will open an explorer window, after which you can just double click the `AnonymousDesktopWallet-1.1.0.jar` executable file.

Alternatively, if you wish to download the latest version, it can be found in the [releases section](https://github.com/anonymousbitcoin/anon-full-node-wallet/releases) of the ANON repo. 

**NOTE:** the file `AnonymousDesktopWallet-1.1.0.jar` **MUST** be placed within the same directory as your `anond` and `anon-cli`. The wallet uses both those compiled binary files to communicate to the blockchain. Without those two files, the wallet **will not** work.

## Windows Guide