# Decentralized Governance on the ANON Blockchain

- [Governance Overview](#overview)
- [Proposals](#proposals)
- [Voting](#voting)
- [Getting Started](#getting-started)
- [Tips for successful proposals](#tips-for-a-successful-proposal)

## Overview

Masternodes on the ANON blockchain do more than just verify transactions. Masternodes and masternode owners, have the ability to vote on, and create proposals to influence the future of the coin for good! 

Decentralized Governance by Blockchain (DGBB), is a feature introduced by [DASH](https://www.dash.org/) as an attempt to solve the problems of governance and funding in the crypto space. Governance is difficult in decentralized projects as there are no central authorities to make decisions for the project, typically all of the decisions will be left to the developers.

Instead of leaving the decisions up to the developers, the responsibility is passed over to masternode owners on the network. Decentralized Governance allows each masternode to vote for or against a proposal, submitted by other masternode owners.

Once a proposal has been passed, it is then vetted by the developers and can be implemented (or not) into the code base by the ANON developers. With the eventual implementation of super blocks, DGBB provides means for the ANON developers to fund their own development. 

**NOTE:** Currently, without the implementation of super blocks, it is not possible to receive funding for a proposal. 

## Proposals

Proposals can be generated easily though the use of the [ANON governance tool](https://proposalgenerator.anonfork.io/). In order to submit a proposal, a payment of 5 ANON is required. This ensures that proposals have some weight behind them and are not scams or memes. Once the fee has been paid, the transaction is **irreversible**. The 5 ANON is then burnt and removed from circulation. Once proposals are live they can not be modified. 

To generate a proposal, the following guidelines must be followed:

- Proposals require an unique proposal name, 20 chars or less.
- The URL of a proposer-created webpage detailing proposal information.
- An ANON address.
- Monthly payment in ANON requested. (Payments yet to be implemented)
- Block start, detailing the requested start of proposal payments. (Yet to be implemented)
- Payment-count detailing the amount of cycles required for proposal requesting payment. (Yet to be implemented)

**NOTE:** Although these features are not implemented yet, they are required to submit an initial proposal.

Proposal persistence

- Proposals become active one day after submission.
- Proposals will remain visible on the network until they are either disapproved or the proposals last payment-cycle is reached.
- The total available votes is the count of online and responding masternodes that can be seen by running the RPC command `masternode count`.

Once passed, proposals are able to report back to the network on the [ANON Discord](https://discordapp.com/invite/9XQMspU) or via published public channels and social media. Proposals that require payout over several months can have their funding revoked if those parties do not live up to their end of the deal. Encouraging honesty and trust to gain approval of the network.

## Voting

Votes are cast by masternode owners. Masternode owners can vote either `yes`, `no` or to `abstain` from the proposal. Votes can be changed at any time as they are only counted at the end of the voting cycle.

In order for a proposal to be approved, it needs a certain number of `yes` votes. The formula works as follows:

`(YES-votes - NO-votes) > TOTAL MASTERNODES/10`

The difference between the `yes` and `no` votes is calculated. This total needs to be greater than 10% of the total amount of masternodes in the network at the end of the voting period.

## Getting started

To generate a proposal navigate to the [proposal generator](https://proposalgenerator.anonfork.io/). 

From there you can generate a proposal similar to the example below:

> ![generator_create_proposal](https://assets.anonfork.io/gov_images/generator_create_proposal.png "Proposal Generator")

The variables required to be filled in are the:

- `Proposal Name` - A unique single word name for your proposal.
- `Proposal Description URL` - Link to the Description website for your proposal.
- `Payment Date` - The date at which payments should be made.
- `Payments` - The amount of payments expected.
- `Payment Address` - The address where the payments will be made to.
- `Payment Amount` - The amount of ANON requested per payment. **NOTE** This address MUST have a minimum balance of 5 ANON for it to be accepted.

Once these values are filled in correctly, you can click the Create Proposal button. After which you will see the following displayed.

> ![wallet_commands_blank](https://assets.anonfork.io/gov_images/wallet_commands_blank.png "Copy the entire text")

The first text box shows an incomplete `Prepared Governance Object`. Copy the entire text contained within the first text box, and open up your ANON wallet. Click on the button that says 'Create New GovObject' in the Governance Objects tab.

It will open a window that looks like this: 

> ![enter_prepare_command](https://assets.anonfork.io/gov_images/enter_prepare_command.png "Wallet Prepare Proposal")

Paste the value from earlier into the first section.

> ![enter_prepare_command_2](https://assets.anonfork.io/gov_images/enter_prepare_command_2.png "Enter the Prepare object into the top text bar")

Now that you have pasted that, click on the 'Prepare Proposal' button. What you will see below is the transaction id:

> ![copy_tx_id_2](https://assets.anonfork.io/gov_images/copy_tx_id_2.png "TX ID is returned from proposal, copy it")

Copy that value and go back to the governance explorer you were at earlier. Now you have the transaction ID from the wallet, you can insert it into the second text box titled 'Transaction ID':

> ![wallet_commands_filled](https://assets.anonfork.io/gov_images/wallet_commands_filled.png "Paste in the transaction you received from the wallet")

Now, click the confirm button. The governance object will need to be processed. You will see a loading screen display stating that you need to wait roughly 1 hour (60 minutes) for the 6 blocks to process.

> ![confirm_transaction](https://assets.anonfork.io/gov_images/confirm_transaction.png "The transaction needs to be confirmed")

After the 6 blocks have been mined you will see that the `GovObject` you submitted has changed from `Prepare` and now contains `Submit` in the text. Copy that whole value and go back to the wallet. 

> ![ready_to_submit](https://assets.anonfork.io/gov_images/ready_to_submit.png "Ready to submit GovObject")

Paste the information into the text box next to the 'Submit Proposal'. **Add a space** and paste your transaction ID and click submit.

> ![submit](https://assets.anonfork.io/gov_images/submit.png "Paste the Submit object followed by your transaction ID")

Once the submit has been processed, you should now see the proposal populate in your wallet.

> ![wallet_ss1](https://assets.anonfork.io/gov_images/wallet_ss1.png "Proposal appears on the wallet")

If you wish to vote for your proposal (or any other proposal), you can click on the `vote-all` or `vote-alias` button. Choose your vote of either `yes`, `no` or `abstain`. It will return confirmation to you such as this:

> ![gobject_voting_result](https://assets.anonfork.io/gov_images/gobject_voting_result.png "Voting result")

Now, your proposal is live! All that's left to do is monitor your proposal, this can be done at the following link: [TODO]().

## Tips for a successful proposal

Proposals in the ANON governance system are subject to voting by masternodes. Meaning, just like in real voting, you need to convince voters that your proposal is legitimate and should pass.

Keep the following points in mind when submitting a proposal:

#### Keep proposals clear

Proposals should have a clear title, accompanied by a short and to the point description of the objectives. Provide information early on explaining why your proposal will benefit the ANON network. Masternode owners should not have to do extensive research to understand what your proposal entails. 

#### Gather proposal feedback BEFORE submission

Pre-proposal discussions are highly recommended before posting. Rushing into the generation of your proposal without thinking it out clearly could result in you losing your 5 ANON and having your proposal buried at the bottom of the list. The 
[ANON Discord](https://discordapp.com/invite/9XQMspU) is a great place to communicate with community members and get an indication of the value and viability of your proposal. 

#### Build a reputation

The ANON community is growing more and more each day, always welcoming new users. Because of the nature of Crypto in general, and how proposals work, trust plays a key role in a successful proposal. Starting small is advised, allowing you to prove your credibility to the community. [Keybase](https://keybase.io/) is a great way for users to build a verified online persona, and in turn, build trust in the community.

#### Be enthusiastic about your proposal!

Proposals with detailed videos or websites have a far greater chance of succeeding. Videos add a personal touch and is a great way to express your proposal in greater detail. Post your media on our telegram, discord or twitter. Always remember, these are people you are trying to convince, so don't be annoying and spam channels begging for votes.

#### Post your proposal early and be available for questioning

When submitting a proposal, you can expect it to be *heavily* scrutinized by masternode owners and ANON core developers. It is critical that you allow enough time for voters and developers to review your proposal before the end of the voting period. Once the voting period is over, no more votes can be counted. You might receive 100% `yes` feedback from masternode voters, but if the total amount of votes received is less than the required amount (as stated [above](#voting)) your proposal will not be accepted, and you will need to resubmit in the next voting period. 

#### Keep the community updated

If your proposal passes, you should keep the ANON community informed! The community has voted for you and are now expecting you to deliver on your commitments. Meet your deadlines, and build the trust of the voting community. Remember, if you fail to make good on your proposal promises, getting your future proposals to pass may prove challenging.
