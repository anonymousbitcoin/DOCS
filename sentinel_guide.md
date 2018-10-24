# Sentinel Update
[![](https://img.shields.io/badge/ANON-1.3.0-green.svg)](https://github.com/anonymousbitcoin/anon/releases/tag/v1.3.0)
[![](https://img.shields.io/badge/Sentinel-v1.1.2-green.svg)](https://github.com/anonymousbitcoin/sentinel/releases/tag/v1.1.2)

Sentinel is an autonomous agent for persisting, processing and automating ANON governance objects and tasks. Sentinel is implemented as a Python application that binds to a local version anond instance on each ANON Masternode.

This update is necessary as it fixes several bugs that were surfaced during the creation of proposals. This update serves to fix those errors ensuring that proposals remain on the network and are not automatically deleted by the Sentinel.

This guide covers updating an already installed version of Sentinel to the newest version [v1.1.2](https://github.com/anonymousbitcoin/sentinel/releases/tag/v1.1.2).

### Update Process

If you have not yet installed sentinel on your masternode, we advise that you follow the guide on the [Sentinel Repo](https://github.com/anonymousbitcoin/sentinel) and install it.

To update, enter the following commands in your VPS where your masternode is located:

```
git fetch 

git checkout master

git reset --hard origin/master

git pull origin master
```

These commands will:

- `fetch` the latest code saved on Github. 
- `checkout` to the correct branch.
- `reset` your code if any changes have been made.
- `pull` the latest changes and update the source code.

This is all that is needed for the update, if you installed Sentinel correctly in the first place, your `crontab` will run the Sentinel for you at the required time.

