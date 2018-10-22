# How to set up Anon for the first time (ON MAC):

Setting up an Anon node can be confusing for first time users. Follow the guide below to ensure your environment is set up and ready.

### Mac:

#### Node Installation:

First, in your terminal install XCode. You can install it using this line:

```bash
xcode-select --install
```

Ensure you have the latest version of Ruby installed on your computer by running:

```bash
ruby -v
```

The current latest version at this time of writing is 2.5.1, but any version 2.3.x will run just fine.

Install **homebrew** on your computer with the following line:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Brew installs all the required dependencies you will need in order to install the repo correctly. The required dependencies can then be installed with the following line:

```bash
brew install cmake autoconf libtool automake coreutils pkgconfig gmp wget
```

The last dependency required is gcc5 and can be installed with the following command: 

```bash
brew install gcc5 --without-multilib
```

Next, assuming that all went well. Clone the repo, run these commands in sequence:

```bash
cd ~

git clone https://github.com/anonymousbitcoin/anon.git
```

This will create a directory called `anon`, you will need to move into that directory using:

```bash
cd anon
```

Once you're in the `anon` directory, run the following script to build the program and create the executables:

```bash
./anonutil/build-mac.sh -j$(sysctl -n hw.physicalcpu)
```

This could take anywhere between 5 and 10 minutes to build depending on your system specifications.

Finally, the ZCash params are needed, they are included in the repo and can be fetched using the following command:

```bash
./anonutil/fetch-params.sh
```

Your node is almost ready! Its time to set up your `.conf` file. The `.conf` file is the configuration file that is required to start up the node correctly. You might have noticed, if you skipped a few steps, that the node won't run unless you've completed the following steps:

#### Configuration File Set Up.

It is important that this file is made in the correct directory. If the file does not exist in the correct path, the node will not build and you will continue to see the same error.

To set this up change into the correct directory.

Run these commands in sequence:

```bash
cd ~

# if you have problems, one of these will work (run only one of these):
cd ~/Library/Application Support/
# or
cd ~/Library/Application\ Support/
# or
cd "$HOME/Library/Application Support/"

mkdir anon

cd anon

touch anon.conf
```

**NOTE:** Should you have a problem changing into the Application Support directory, simply open it up in finder and make the anon folder there, and create the file as you normally would any other file.

Inside that directory, you will now have an `anon` directory with an `anon.conf` file. Open that file either in vim, or your favorite text editor.

To open in vim:

```bash
vi anon.conf
```

If you dont know how to use vim, you can open it with any other text editor you have.

```bash
# using vs code
code anon.conf
# or atom
atom anon.conf
# or sublime text
subl anon.conf
```

Or simply right click the file and open with default.

Inside that file, you will need the following lines:

```bash
rpcuser=your-username
rpcpassword=set-a-password-dont-use-this-one-you-will-lose-your-money-9sad8f90a8sd7f098as
rpcallowip=127.0.0.1
txindex=1
```

Save that file and go back into your Anon directory that you cloned earlier.

```bash
cd ~/anon
```

If everything up until this point has worked for you. Congratulations, you are now ready to run your node. The following command will start the node and boot up the testnet. 

```bash
./src/anond
```

Please give plenty of time for the blocks to download. If you are experiencing problems, take a look at the log files for more information (you might need to add `debug=1` to your anon.conf file).

Thank you for supporting Anonymous Bitcoin.

Please stay tuned for more files like this to come for both Linux and Windows users.