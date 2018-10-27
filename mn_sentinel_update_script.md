# Update Masternodes and Sentinel

[![](https://img.shields.io/badge/ANON-1.3.0-green.svg)](https://github.com/anonymousbitcoin/anon/releases/tag/v1.3.0)
[![](https://img.shields.io/badge/Sentinel-v1.1.2-green.svg)](https://github.com/anonymousbitcoin/sentinel/releases/tag/v1.1.2)

It is required to update your masternodes and sentinel periodically. We at ANON know this can be a hassle for some people so we've comprised a short script to help speed things along.

SSH into your VPS where your masternode is located, in the root directory, paste this whole segment of code:

**PLEASE NOTE, THIS SCRIPT WILL ONLY RUN IF YOU ARE ROOT USER!!** Please check back soon for the **NON-ROOT** guide and script.

```bash
pkill anond && \
rm -rf Anon-full-node-v1.3.0-linux.tar.gz && \
rm -rf anond anon-cli && \
wget https://github.com/anonymousbitcoin/anon/releases/download/v1.3.0/Anon-full-node-v1.3.0-linux.tar.gz && \
tar -xvf Anon-full-node-v1.3.0-linux.tar.gz && \
mv anond /usr/bin/ && \
mv anon-cli /usr/bin/ && \
rm -rf Anon-full-node-v1.3.0-linux.tar.gz && \
sleep 10 && \
anond -daemon && \
sleep 20 && \
anon-cli getinfo && \
anon-cli masternode status && \
cd ~/sentinel && \
git fetch && \
git checkout master && \
git reset --hard origin/master && \
git pull origin master
```

After pasting this, your masternode should be fully updated. You can check that the script worked with the following:

For ANON:

```bash
#check status in anon folder
cd ~/anon

#check git logs
git log

```

At the top, you should see the commit:

```bash
commit 541c67c97c26ffc3bdc40a2db37703059b7dfdf7 (HEAD -> master, origin/master, origin/HEAD)
Merge: 04b22f51c 46379f3e9
Author: thedon_chris <30728737+thedon-chris@users.noreply.github.com>
Date:   Tue Oct 2 19:15:32 2018 -0400

    Merge pull request #67 from anonymousbitcoin/fix/seeders

    Remove dead seeders from mainnet
```

For Sentinel

```bash
#check status in sentinel folder
cd ~/sentinel

#check git logs
git log
```

At the top, you should see the commit:

```bash
commit 023ac0d062dfdd17863e6e6095afa6d8bc8b1433 (HEAD -> master, tag: v1.1.2, origin/master, origin/HEAD)
Merge: d07faf5 4cba070
Author: nlevo <18757529+nlevo@users.noreply.github.com>
Date:   Tue Oct 23 09:31:30 2018 -0700

    Merge pull request #11 from anonymousbitcoin/v.1.1.2

    Update version to v1.1.2
```

If you see those commits at the top, you are up-to-date!

This guide is valid as of 20 October 2018.