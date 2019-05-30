# Glitch-soc for YunoHost
  
[![Install Glitch-soc with YunoHost](https://install-app.yunohost.org/install-with-yunohost.png)](https://install-app.yunohost.org/?app=glitch-soc)

*[Lire ce readme en français.](./README_fr.md)*

> *This package allow you to install Glitch-soc quickly and simply on a YunoHost server.  
If you don't have YunoHost, please see [here](https://yunohost.org/#/install) to know how to install and enjoy it.*

:warning: This application uses the Debian backports packages, do not install this application directly in production

## Overview
Glitch-soc is a free, open-source social network. A decentralized alternative to commercial platforms, it avoids the risks of a single company monopolizing your communication. Pick a server that you trust,whichever you choose, you can interact with everyone else. Anyone can run their own Glitch-soc instance and participate in the social network seamlessly.

**Glitch-soc is a friendly fork of [Mastodon](https://joinmastodon.org/), mainly similar but with some extra features.**

This app is a fork of [Yunohost Mastodon app](https://github.com/YunoHost-Apps/mastodon_ynh), with extra changes for Glitch-soc. It will be kept up-to-date with Yunohost Mastodon repository.

**Shipped version:** 2.8.3 Mastodon equivalent

*NB: Glitch-soc doesn't provide any specific release, and is constantly updated. We try to use it at a state that correspond to the equivalent Mastodon version.*

## Screenshots

![](https://framalibre.org/sites/default/files/mastodon.png)

[Source code](https://github.com/glitch-soc/mastodon/)

## Configuration

#### Adding "swapfile" If you have less than 2Go of RAM
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=1024000
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```
add this line on /etc/fstab
```
/swapfile       none    swap    sw      0       0
```

### Install

#### Domain

You can't install Glitch-soc in subdirectory, you must use a domain or subdomain for this application.

#### Using __screen__ in case of disconnect
```
sudo apt-get install screen
screen
sudo yunohost app install https://github.com/YunoHost-Apps/glitch-soc_ynh.git
```
Recover after disconnect:
```
screen -d
screen -r
```
The admin user is automatically created as: user@domain.tld

### Update
#### Using __screen__ highly recommended

`sudo yunohost app upgrade --debug glitch-soc -u https://github.com/YunoHost-Apps/glitch-soc_ynh.git`

### Migration from Mastodon

In theory, you can upgrade your mastodon instance to glitch-soc just by upgrading the sources. Then it's possible to upgrade you Mastodon Yunoost instance like this :
`sudo yunohost app upgrade --debug https://github.com/YunoHost-Apps/glitch-soc_ynh`

:warning: Do that at your own risk, and make some backups first :)

## Recommendation

It seems important to close the inscriptions for your Glitch-soc, so that it remains a private body. We invite you to block remote malicious instances from the administration interface. You can also add text on your home page.

## Documentation

 * Official documentation: https://glitch-soc.github.io/docs/

## YunoHost specific features

#### Supported architectures

* x86-64b
* Jessie x86-64b
* ARMv8-A : :warning: This app can work on ARM, but installation takes several hours and you must add a swapfile of 1GB.


## Links

 * Report a bug: https://github.com/lapineige/glitch-soc_ynh/issues
 * App website: https://glitch-soc.github.io/docs/ (and https://joinmastodon.org/ for Mastodon)
 * Upstream app repository: https://github.com/glitch-soc/mastodon
 * YunoHost website: https://yunohost.org/

---

Developers info
----------------

:warning: For any change that is *not* glitch-soc specific, **please contribute first** to [Mastodon app repository](https://github.com/YunoHost-Apps/mastodon_ynh). Then these changes will be merged in this repository.

Please do your pull request to the testing branch.

To try the testing branch, please proceed like that.
```
sudo yunohost app install https://github.com/lapineige/glitch-soc_ynh/tree/testing --debug
or
sudo yunohost app upgrade glitch-soc -u https://github.com/lapineige/glitch-soc_ynh/tree/testing --debug
```
### How to upgrade Glitch-soc version

Go to Mastodon source code repository, find out in the [release](https://github.com/tootsuite/mastodon/releases/) part on in the dedicated branch what is the latest commit of this branch.
Then go to Glitch-soc repository, find the very same commit in the [commits list](https://github.com/glitch-soc/mastodon/commits/master).
Then you can use change the source to this commit.
