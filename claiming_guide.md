# How to claim BTC in ANON

### Using Mnemonic passphrase:

Ensure you have your mnemonic pass phrase for your wallet. This can be the 12 or 24 letter phrase you (hopefully) wrote down when you created you wallet for the first time.
(If you've lost your passphrase, sorry...)

[Using this offline tool](https://github.com/iancoleman/bip39), enter your mnemonic phrase. FOLLOW ALL SECURITY GUIDELINES EXPRESSED IN THE REPO ITSELF!! MAKE SURE YOU HAVE YOUR INTERNET CONNECTION DISABLED!! 

Enter your BIP39 Mnemonic. Ensure you select BTC - Bitcoin in the Coin section.

Beneath you will see Account Extended Private/Public Keys. These keys are extended, meaning they encapsulate.........

Scroll down further and set the Derivation Path to BIP49.

Below you will see a table of:

`Path, Address, Public key, Private Key`

If you know your address, match it to one in the list. If you do not know your address, you will need to try several of them until you find the correct one.

This can be done quickly by entering your EXTENDED PUBLIC KEY in [blockchain.info](https://www.blockchain.com/explorer). This should find any and all addresses you have used that relate to that extended key.

Once you have determined which of the addresses contains the funds, go into your Anon Full Node.

With the daemon running, and your node synced to the network. Run the following command:

`./src/anon-cli -testnet importprivkey <your_priv_key>`

Once you have entered that command, you may need to wait several minutes for the entire blockchain to be scanned and find your address.

After several minutes, enter the following command:

`./src/anon-cli -testnet getbalance`

This command should display your balance that you had your BTC account.