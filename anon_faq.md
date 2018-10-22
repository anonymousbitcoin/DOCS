# ANON FAQ

Welcome to Anon! We understand that running nodes through the terminal can be challenging even for experience developers. This guide should help you with commands and tricks and get the most out of your Anon Full Node!

This list is comprised of the most commonly asked questions. If you have a different issue or question. Contact the ANON team directly at our [issues page,](https://github.com/anonymousbitcoin/anon/issues) and we can answer them for you, and add them to this list.

## How do I build/compile the node?

To build the node, follow the instructions in the [readme](https://github.com/anonymousbitcoin/anon/blob/master/README.md), the instructions are different for each operating system. A full list of the documentation can be found [here](https://github.com/anonymousbitcoin/anon/tree/master/doc). 

A beginner guide for MAC users has been posted [here](https://gist.github.com/kaypon/4e6863e26f21fca9f5b8b350350912a1).

The same guide is WIP for Linux.

## Where should I store my `anon.conf`?

For Mac: inside the folder `Anon` which is contained in your `/Library/Application Support/Anon/`

For Linux/Windows: in your root directory, you have to create a hidden file `.anon`.

## What should I have in my `anon.conf`?

Normally, these files can be totally empty. They just have to exist! However, the following lines are beneficial to have:

```{r, engine='bash'}
rpcuser=anything-you-want
rpcpassword=set-a-password-or-you-will-lose-your-precious-anon
rpcport=127.0.0.1
txindex=1
testnet=1
```

`testnet=1` tells the system that we are running in testnet.

Be smart, change your password. It is very easy for malicious actors to steal your information if you are not careful.

For the full list of commands you can store in your `anon.conf` follow this link [here](https://github.com/anonymousbitcoin/anon/blob/master/contrib/debian/examples/anon.conf)

## How do I start the daemon?

Starting the daemon is easy! Assuming you have built and compiled the code, change directories into where you cloned the repo with:

```{r, engine='bash'}
cd ~/path/to/anon/
```

Inside the root of that directory enter the following:

```{r, engine='bash'}
./src/anond -testnet
```

This will start up the node and you will see the ascii logo for ANON. **NOTE:** if you have the line `testnet=1` in your `anon.conf` you do not need to add the `-testnet` flag when running the node. 

If you wish to hide the ANON ascii logo, you can add the flag `-daemon`. This will hide the metrics page and allow you to work in the same terminal. **NOTE:** this will run the node in the background. Check below to see how to stop the node in the background.

After stopping your node, and starting it up again, you may notice that it fails to run. To solve this add the `-reindex` flag.

```{r, engine='bash'}
./src/anond -daemon -reindex
```

## How do I stop the daemon?

There are three ways to stop the daemon. 

The first is to simply press `ctrl + c` in the metrics page. This will stop the node safely, it might take a few seconds to go through the shutdown process.

The second option is through the `anon-cli` and can be done like this:

```{r, engine='bash'}
./src/anon-cli -testnet stop
```

The stop command will kill the node and shut down normally. It is important to add the `-testnet` flag.

The final option is to kill the running process by entering:

```{r, engine='bash'}
ps aux | grep anond
```

That will search for ALL running processes, and return only the ones with the text `anon`. The command will return something like this:

```{r, engine='bash'}
yourname  92731   0.2  0.1  4338144  12360 s005  SN+  10:38AM   2:00.27 ./src/anond -testnet -reindex
```

The second variable, after your computer name is the `PID`. To stop the process enter:

```{r, engine='bash'}
kill <pid_number>
```

This will instantly kill the node, without giving it time to do its proper shutdown process. This can be dangerous, and should a last resort.

## How do I use the CLI?

The cli has many powerful commands that can be used to interact with the node. To run commands through the cli enter the following:

```{r, engine='bash'}
./src/anon-cli -testnet [command]
```

A full list of the commands can be retrieved by entering

```{r, engine='bash'}
./src/anon-cli -testnet -help
```

**LIFEHACK:** to make things easier for you, set up an **alias**! This will speed things up for you as you will no longer need to type the full `./src/anon-cli -testnet`. This can be done by:

```{r, engine='bash'}
alias anCLI="./src/anon-cli -testnet"
```

You can change the `anCLI` to anything you like! Now you can enter commands like:

```{r, engine='bash'}
anCLI getinfo
anCLI getbalance
anCLI [command]
```

**NOTE** THE REMAINDER OF THIS DOCUMENT WILL USE THE `anCLI` INSTEAD OF THE `./src/anon-cli -testnet`.

More advanced users can add these aliases to their zsh or bash profiles. But we will skip that for now, its easy to do with a google search!

## How do I run the wallet?

The wallet can be downloaded from [here](https://github.com/anonymousbitcoin/anon-full-node-wallet/releases). The wallet requires that you have built the full node already.

Once you've installed the node, and downloaded the wallet, move the AnonymousDesktopWallet-1.0.jar into the same folder (`src`) that `anond` and `anon-cli` are kept. Once its there, either double click it or run the following command:

```{r, engine='bash'}
java -jar AnonymousDesktopWallet-1.0.jar
```

The wallet will start your ANON node, if its not already running. Please note the wallet is still in development. It may not behave as expected.

## How can I check my balance?

When you run the first time, an address is automatically generated for you. To take a look at all your addresses enter the following:

```{r, engine='bash'}
anCLI listaddressgroupings
# or for a more detailed list
anCLI listreceivedbyaddress
```

This should return you something like this or multiple:

```{r, engine='bash'}
  {
    "address": "tAJJujnotarealanonaddressJtAA419F3FM",
    "account": "",
    "amount": 10.00000000,
    "confirmations": 522,
    "txids": [
      "15c39a9140a47c19470d3d08b9ceb9f5fb18cfdfbdf09ac4862070e8979"
    ]
  },
```

To check your balance run the following command 

```{r, engine='bash'}
anCLI getbalance [address]
#example:
anCLI getbalance tAJJujnotarealanonaddressJtAA419F3FM
```

You do not need to add the `address` part, omitting it will show your full balance. Adding the address will show you the balance contained in that address.

## How do I send/receive ANON?

To receive anon, copy one of your existing addresses or create a new one! This can be done with the command:

```{r, engine='bash'}
anCLI getnewaddress
```

This will return you an address. Please note that ALL testnet addresses begin with `tA`. 

To send anon, you will need the address from someone you wish to send funds to. Once you have received their address run the following command:

```{r, engine='bash'}
anCLI sendtoaddress [address] [amount]
#example
anCLI sendtoaddress tAJJujnotarealanonaddressJtAA419F3FM 10
```

The second command will send 10 ANON to the address `tAJJujnotarealanonaddressJtAA419F3FM`.

After you enter the command, a `transaction hash` is returned. It will look something like this: `3f19e1fd8f6c0945f6744669034d7987bd72bac10ae0709caf1a2a69d8062fa8`. With that hash, you can look deeper into it with the command:

```{r, engine='bash'}
anCLI gettransaction [txhash]
#example
anCLI gettransaction 3f19e1fd8f6c0945f6744669034d7987bd72bac10ae0709caf1a2a69d8062fa8
```

This will return the transaciton information and should look something like this:

```{r, engine='bash'}
{
  "amount": -10.00000000,
  "fee": -0.00000669,
  "confirmations": 1,
  "blockhash": "00001481d02ad4fbb6f253d9cf2133a0a6abcf97b2b54cb3a244e8b47cde3a9e",
  "blockindex": 3,
  "blocktime": 1535742654,
  "txid": "3f19e1fd8f6c0945f6744669034d7987bd72bac10ae0709caf1a2a69d8062fa8",
  "walletconflicts": [
  ],
  "time": 1535736248,
  "timereceived": 1535736248,
  "vjoinsplit": [
  ],
  "details": [
    {
      "account": "",
      "address": "tACqigfawR5U2Pmoq5Uahn7ZxTy6aRY5hvV",
      "category": "send",
      "amount": -10.00000000,
      "vout": 1,
      "fee": -0.00000669,
      "size": 668
    }
  ],
  "hex": "010000000445a1403120fabe008a9f317f1b2fc2ac4b751de010000006b4830450221008b01efc1106861574aa5db73362b1cbd9be8c9ecd8255dbb87b8086aaca95dcf022037ec2d7fb2b14ae94508f8c7defa72f12ad97d2a952c152d99a0447c6b5cd02201e80058cd6c92240a3acff1f4c9c0b57eed414590bf314432ccf30a35c1ac6fb412102fbcc6698a5209c5ff7c7b9a824de35129de376367a7f9582e496935b415cd359feffffff0223d25407000000001976a914002b6c8e76536d4685d2d019a6cbbd68ea7c485c88ac005ed0b2000000001976a921e41210237d67f1fb95f1e6e05da73fdbea1f5fae43bc63a3e627d42797ed355029a546dfeffffff45c659ef51515a0ec610f1ba49950cd1ac2a87a4894bdb4f051436cb7833cd2d010000006a473044022004d405717b7ce1abe589913370246605688c501c9973095120b7bc4d8e580a6602a937426059850e5ac3c228d02205259bf9b73575d262974fd08067cbf55be0c830b7458b6eb1a0ad1b7c30b19ef412102190a773ee24e7c629410ad1ffeaa57417b202da7fa3f1893c70818c1868a8731feffffff6c143fb7ea66bda1374fa8680dd21a115d9fb0330c7c127861b4837c437bf249010000006a47304402206362e636a3dd6474734c6ec53eb8293dc8dad6c5022b8009212a1a5985b2b1c3022016c881df6c8a20ddf166e0beb1353b099ed7aa19fc1d1fd9c4355425dbbc99164121039611ae7ea92c7efbfcb489b0c3522335385ccefd657e6f604c94b30dbe2ba162feffffff79890e076248ac09dffb18fbf5b9ceb9083d0d47197ca44091da8c323f9cc315010000006b483045022100d82d1a962ff960192b90e874d59f36ba3fcde4c969cbc174cfb3e1223674c1111426bde041738cc4b420e911c968798366be75ca5888ac07070000"
}
```

**NOTE:** You will need to wait a few minutes for the transaction to get mined before you can spend the ANON.

## How do I get back to the ASCII ANON page?

When you start the node without the `-daemon` flag, the metrics will appear looking like this:

```{r, engine='bash'}
           Block height | 1811 (100.00%)
            Best header | 1811
            Connections | 8
  Network solution rate | 383 Sol/s
```

Once you close that terminal window, the process will remain running in the background. Currently there is no way to retrieve this page again without restarting the node. However, there is a more usefull but less pretty alternative!

Run a watch! This can be done by entering the following command (**NOTE:** your aliases will not work).

```{r, engine='bash'}
watch -n 1 ./src/anon-cli -testnet getinfo
```

This will run the command `./src/anon-cli -testnet getinfo` every second. It will constantly update and show you the latest response. The result should look something like this:

```{r, engine='bash'}
{
  "version": 1001251,
  "protocolversion": 180004,
  "walletversion": 60000,
  "balance": 1002.22999331, (rWARNING: check your network connection, 1 blocks received in the last 4 hours (24 expected)
  "blocks": 1811,
  "timeoffset": 0,
  "connections": 8,
  "proxy": "",
  "difficulty": 9568.695262002WARNING: check your network connection, 1 blocks received in the last 4 hours (24 expected)
  "testnet": true,
  "keypoololdest": 1534882413,WARNING: check your network connection, 1 blocks received in the last 4 hours (24 expected)
  "keypoolsize": 101,
  "paytxfee": 0.00000000,
  "relayfee": 0.00001000,
  "errors": ""
}
```

To stop the watch, just press `ctrl + c`.

## I have two wallets. How can I import my wallet/address into my current one?

This is done simply. However, exposing private keys can put you in danger of losing your funds. This is not a big deal in testnet, but when main net is launched, its your money. It is very easy to lose your money if you do not take the necessary precautions. 

Now that you know how to get your address, you can get your private key! This is done by taking your address and entering the following command:

```{r, engine='bash'}
anCLI dumpprivkey [anonaddress]
#example
anCLI dumpprivkey tAJJujnotarealanonaddressJtAA419F3FM
```

This will return your private key. Please, don't share this address. Please.

The response will look something like this:

```{r, engine='bash'}
cVqe2ox1YTinvalidjzpCR7jab4RgTAprivkeyD6mF8mgzoAshsbu1UZj
```

Great! Thats your privat key! Don't save this anywhere in your computer (really, I cannot stress the importance of keeping this information **PRIVATE!!**).

Now that you have the private key, you can go to your other wallet and import it there with the following command:

```{r, engine='bash'}
anCLI importprivkey [private key]
#example
anCLI importprivkey cVqe2ox1YTinvalidjzpCR7jab4RgTAprivkeyD6mF8mgzoAshsbu1UZj
```

```{r, engine='bash'}
Depending on the height of the blockchain, this can take anywhere between a couple minutes to a few hours! It has to scan the **entire** anon blockchain to find where your private key has been used. Once this address has been found the funds inside there are now considered to be yours and can be spent.

## Theres a new update to ANON!? How do I update?

We plan to keep ANON as up-to-date as possible. We will always anounce a new version and inform users before hand. Unless specified, being behind a few versions should not affect your node. Your wallet will never be compromised during updates.

To check the status, you will need to run a few git commands. Git is a software version control solution used to store massive software files, its where you got the files to install the node! To check if your node is using the latest code run the command:

```{r, engine='bash'}
git fetch --all
git status
```

If you are on the latest version you should see something similar to the following:

```{r, engine='bash'}
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

Nice! You're running the latest version of ANON! If you see something different like this:

```{r, engine='bash'}
Your branch is behind 'origin/master' by 21 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)
```

If you see this, you will need to pull the latest changes. This can be done by entering the following command:

```{r, engine='bash'}
git pull origin master
```

Done successfully, you should see a response similar to this.

```{r, engine='bash'}
remote: Counting objects: 69, done.
remote: Compressing objects: 100% (18/18), done.
remote: Total 69 (delta 46), reused 63 (delta 46), pack-reused 5
Unpacking objects: 100% (69/69), done.
From https://github.com/anonymousbitcoin/anon
 * branch                master     -> FETCH_HEAD
   ddaf84bd9..eb3cf9c4e  master     -> origin/master
Updating 6ce1f797b..eb3cf9c4e
Fast-forward
 MNUpdaterTestnet.sh         | 67 +++++++++++++++++++++++++++++++++++++++++++++
 README.md                   | 45 ++++++++++++++++++++++++++++++
 nodeUpdaterTestnet.sh       | 27 ++++++++++++++++++
 src/darksend.cpp            |  2 +-
 src/main.cpp                |  3 +-
 src/masternode-payments.cpp |  2 +-
 src/masternode-payments.h   |  4 +--
 src/masternode-sync.cpp     | 18 ++++++------
 src/masternodeman.cpp       |  2 +-
 src/miner.cpp               |  2 +-
 src/rpcclient.cpp           |  2 ++
 src/rpcmining.cpp           | 57 +++++++++++++++++++++++++++++++-------
 src/sync.cpp                | 23 ++++++++++------
 src/test/rpc_tests.cpp      |  7 +++++
 14 files changed, 226 insertions(+), 35 deletions(-)
```

If, for some reason, you have made changes, you will either have to commit them and make a pull request to ANON. These changes will then be reviewed by our developers and if they are worthwhile, possibly added to the core code. If you wish to make a pull request checkout this [link](https://github.com/anonymousbitcoin/anon/blob/master/doc/developer-notes.md). **Note:** this is for advanced developers. In order to pull new changes you will either need to stash your changes, or reset. This can be done by entering the following command:

```{r, engine='bash'}
#to stash changes:
git stash
#to reset
git reset --HARD
```

From there you should have no problem pulling as mentioned earlier. With the latest changes, you can recompile the node quickly, without having to go through the initial setup. Simply typing the following command will rebuild the node:

```{r, engine='bash'}
make -j x
```

Where `x` is the amount of RAM you have on your system divided by 2.

## I want to enter the matrix and see the 'logs'. How do I do this?

There's a lot of information stored in the log files. While the node is running, important information is constantly being appended to the `debug.log` file. At any time you can print out the `debug.log` and view them. However, using the `tail` command from earlier, is more beneficial as you can see the information being displayed in real time.

The `debug.log` file is stored in the same place as your `anon.conf` file in a folder called `/testnet4/`. To get to it enter the following command:

```{r, engine='bash'}
cd testnet4
tail -f debug.log
```

To get more information out of the log file. Append the following line to your `anon.conf`:

```{r, engine='bash'}
debug=1
```

This will tell the daemon to forward all the log information. There is a lot of information there, and can be overwhelming, but the more you look at it the more it makes sense.
