# Anonymous full spec sheet

## Official Release Dates

The official release dates for the ANON blockchain are as follows:

|Network |Release Date|
|:-	|:-	|
|   Test Net	| 10 August 2018	|
|   Main Net |   10 September 2018	|

## Coin Name

The name of the coin is ANON and the ticker for exchanges is $ANON.

## Code Bases

ANON utilizes code bases and technologies developed by [Bitcoin (BTC)](https://github.com/bitcoin/bitcoin), [Zclassic (ZCL)](https://github.com/z-classic/zclassic), [Bitcoin Private (BTCP)](https://github.com/BTCPrivate/BitcoinPrivate), [Dash (DASH)](https://www.dash.org/), [ZCash (ZEC)](https://z.cash/) and [BitcoinZ (BTCZ)](https://btcz.rocks/).

## Privacy Feature

ANON utilizes MIT's tested [ZK-Snarks](https://z.cash/technology/zksnarks) technology. ZK-Snarks is implemented for zero knowledge transactions ensuring the most secure privacy protocol to date.

## Consensus

ANON's blockchain consensus is [Proof-of-Work](https://en.wikipedia.org/wiki/Proof-of-work_system).

## POW

The Proof-of-Work algorithm used in the ANON blockchain is [equihash](https://en.wikipedia.org/wiki/Equihash). The params and personalization string for equihash on the ANON network are the following:

|Network|Equihash Params|Personalization String|
|:-	|:-:	|:-:	|
|   Main Net	|   `144_5`	| `AnonyPoW` |
|   Test Net	|   `200_9`	| `AnonyPoW` |

Because of the `200_9` equihash parameters, testnet blocks are significantly easier to mine.

## Airdrop period

8 hours after the fork. The airdrop heights for both Bitcoin and Zclassic are:

|Coin |Block Height|
|:-	|:-:	|
|   Bitcoin	|   [`540,870`](https://blockexplorer.com/block/000000000000000000183af0c55abab7c0a38e498b843942784182b57309d14c)	|
|   ZClassic	|   [`382,307`](http://explorer.zclmine.pro/block/00000000854e8a49a535674674e1dfe284aff8bf9485fd6bbfa4cf94c8588210)	|

These blocks were mined at Sep 10, 2018 8:59:09 PM, and Sep 10, 2018 9:00:25 PM respectively.

**NOTE:** When syncing a full node, downloading these blocks can take upwards of 10 hours. This is because each UTXO is validated during the download. To speed up initial sync, the bootstrap can be downloaded on the ANON [Assets website](https://assets.anonfork.io/).

## UTXO pay out ratio

ANON snapshotted [UTXO's](http://learnmeabitcoin.com/glossary/utxo) from both the Bitcoin and ZClassic blockchain. Any user who held coins in a wallet before the snapshot, can import their private keys into the ANON blockchain and receive payouts as specified below:

|Coin |Ratio|
|:-	|:-:	|
|   Bitcoin	|  1:1	|
|   ZClassic |   1:2	|

Meaning that users will get a 1 to 1 payout of Bitcoin, and a 1 to 2 payout (double) of their ZClassic. Links to the FAQ on the ANON website can be found [here](https://www.anonfork.io/#faqs).

## Magic

Network magic, also known as the Start String, are the four defined bytes which start every message in the ANON P2P protocol.

The network magic is different for both Mainnet and Testnet

|Network |Magic|
|:-	|:-:	|
|   Main Net	|   `83D847A7`	|
|   Test Net	|   `a345f369`	|

## Ports

#### Network Ports 

|Network|Port Number|
|:-	|:-:	|
|   Main Net	|   `33130`	|
|   Test Net	|   `33129`	|

#### RPC Ports

|Network|Port Number|
|:-	|:-:	|
|   Main Net	|   `3130`	|
|   Test Net	|   `3127`	|

## Prefixes

Address prefixes define the initial starting letters of each ANON Transparent and Private address. 

#### Mainnet:

|Address|Start Prefix|
|:-	|:-:	|
|	Transparent (A)	|	`An`	|
|   Private (Z)	|   `zc`	|
|   Private Key	|   `5` / `K` / `L`	|
|   Script Address	|   `3Z`	|

#### Testnet:

|Address|Start Prefix|
|:-	|:-:	|
|	Transparent (A)	|	`tA`	|
|   Private (Z)	|   `zt`	|
|   Private Key	|   `9` / `c`	|
|   Script Address	|   `t2`	|

## Maximum coin supply

The maximum supply of ANON available is hard capped at 45,500,000.

## Coinburn

Coinburn is done to ensure the health of the current coins in circulation. All UNCLAIMED coins that were airdropped from Bitcoin and ZClassic on the 9/10 fork that are NOT claimed, will be considered unusable. 

The **scheduled** coin burn date is set to **Block height: 37,000**. Which falls within the month of **January 2019**. (With an average block time of 10 minutes, this block falls around the date 26 January 2019.)

**NOTE:** Coinburn only pertains to Main net as there are no airdropped blocks in testnet.

## Block Time and Difficulty Adjustment

Block times for both main net and testnet strives for a consistent 10 minute difference between blocks.

The ANON blockchain modifies [difficulty](http://learnmeabitcoin.com/guide/difficulty) every block, taking the previous 17 blocks into consideration to formulate an acceptable difficulty to match block times. It is possible that some blocks are mined significantly faster/slower than others, as a result of increased/decreased hashing power being introduced/removed on the network.

## Block size

Block sizes for both main net and testnet are 1MB (megabyte)

## Block Rewards

Each block rewards an initial 50 ANON(before [halving](#halving-period)). The subsidy is divided between the miners and masternode stakeholders. 

|Payee |% of Block Rewards|
|:-	|:-:	|
|   Miners	|   65%	|
|   Masternodes	|   35%	|

## Coinbase Maturity

Coinbase maturity defines the amount of time that a coin can be spent after once it has been generated in a new block. Coins created in each block can only be spent 100 blocks after its conception. This ensures that coins that originate from orphaned blocks are considered stale before they are able to be spent, resulting in no false transactions.

|Network|Blocks|
|:-	|:-:	|
|   Main Net	|   `100 Blocks`	|
|	Test Net	|	`100 Blocks`	|

## Coinbase Protection

In ANON, coinbase is protected. This means that funds that are mined and passed the 100 block maturity point **must** be sent to a different address before they can be spent. The address required to be sent to is a Z address. Once the coinbase funds have been moved out of their original address, they are then free to be spent as usual. 

## Halving period

The block reward halving period is the point where the amount of ANON returned in a newly mined block is HALVED. This is set to occur every 134,000 blocks, equating to about 30 months, whereby the subsidy will be halved from 50 ANON per block to 25 ANON per block, and so on.

It is important to note that the first halving will not be on the 134,000th block but instead 134,000 blocks after the airdrop period. The first mined ANON block was block [`16,741`](https://explorer.anonfork.io/insight/block/d401ba877222fe0aca4c3a04b635694da46edc52d13e73437b7ab3be15a93d98), meaning that the first halving will occur on the block `16,741 + 134,000 = 150741`. 

The same payout percentages for miners and masternode still apply.

## Masternode Information

In order to create a masternode, a collateral amount of 500 ANON is required. A masternode is required to run constantly 24/7, and have a static IP.

For governance, to submit a proposal a user will be required to pay a fee of 5 ANON to generate the proposal.

## Additional information

|	Feature	|	Included	|
|:-	|:-	|
|	Replay Protection	|	Yes	|
|	Shielded Transactions	|	Yes	|
|	Closed Premine	|	No	|
|	Community Driven	|	[Yes](https://www.anonfork.io/#community)	|
|	Decentralized Governance	|	Yes	|
|	Dedicated Development Team	|	[Yes](https://www.anonfork.io/#team)	|
|	Slow Start	|	No	|

## Links

|	Link	|	Description	|
|:-	|:-	|
|	[Source Code](https://github.com/anonymousbitcoin/anon/releases)	|	Source code for the ANON blockchain	|
|	[Block Explorer](https://explorer.anonfork.io/insight/)	|	Main block explorer for the ANON blockchain	|
|	[Masternode Explorer](https://explorer.anonfork.io/insight/masternodes)	|	View the status of all masternodes on the network	|
|	[Proposal Explorer](https://explorer.anonfork.io/insight/govobjects)	|	Browse all proposals on the network	|
|	[Governance Explorer and Proposal Generator](https://proposalgenerator.anonfork.io/)	|	Generate proposals on the ANON network	|
|	[Full Node Wallet](https://github.com/anonymousbitcoin/anon-full-node-wallet/releases)	|	Github link to the Full-Node-Wallet	|
|	[Paper Wallet](https://paperwallet.anonfork.io/)	|	Paperwallet generator. (use offline)	|
|	[Website](https://www.anonfork.io/)	|	ANON landing page	|
|	[Responsible Disclosure Policy](https://www.anonfork.io/disclosure)	|	Information regarding disclosure of vulnerabilities	|
|	[Test Net Block Explorer](https://texplorer.anonfork.io/insight/)	|	Block explorer for the Test Net network	|
|	[Twitter](https://twitter.com/ANON_WeAreANON)	|	Official Twitter profile for ANON	|
|	[Telegram](https://t.me/anonymousbitcoin)	|	Official Telegram channel for ANON	|
|	[Discord](https://discordapp.com/invite/9XQMspU)	|	Official Discord server for ANON	|
|	[Reddit](https://www.reddit.com/r/AnonymousBitcoin/)	|	Official subreddit for ANON	|
|	[LinkedIn](https://www.linkedin.com/company/anonymous-bitcoin/)	|	Official LinkedIn Profile for ANON	|
|	[YouTube](https://www.youtube.com/channel/UCU-BMMTH8z0ow0xHjWZHRUg)	|	Official YouTube channel for ANON	|
|	[Miner Info](https://miningpoolstats.stream/anonymous)	|	Unofficial mining pool stats for ANON	|
|	[Zeltrez Block Explorer](https://explorer.anon.zeltrez.io/)	|	Alternative block explorer thanks to [ZelTrez](https://zeltrez.io/)	|
|	[SLIP-44 Pull Request](https://github.com/satoshilabs/slips/pull/398)	|	Official repository of SLIP-044 (for mnemonic phrase generation)	|


