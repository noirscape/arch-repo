## noirscapes arch linux repo

This repository just holds some packages from the AUR that I feel are useful, have broken PKGBUILDs or that I have some matter in terms of maintaining.

## Packages

### Multiple archs

* wget-lua - Hosted because I maintain it.
* fatattr-git - Hosted because I maintain it.

### x86_64 only

* ~~libc++ (and related) - Hosted because default build includes a check() that runs ever single test.~~ Removed: Package is no longer needed for my use case.
* ~~glib2-static-nocheck - **THIS IS A PACKAGE BUILD WITHOUT THE CHECK BECAUSE THE CHECK FAILS**. Provides the glib2-static package on version 2.58.2-2. If glib2-static updates, this package will be superseded. Hosted because nochecks are annoying plus the package is _slightly_ broken due to these failing checks. Only 2 checks fail and they aren't needed for my use case, so I'm not too worried.~~ Removed: Package was updated.
* deluge - This package is _build version boosted_. It will automatically be superseded when the next release for deluge is released. It is a build of commit [3f9ae337932da550f2623daa6dedd9c3e0e5cfb3](https://git.deluge-torrent.org/deluge/commit/?h=develop&id=3f9ae337932da550f2623daa6dedd9c3e0e5cfb3). This commit was selected because it fixes a [major bug](https://dev.deluge-torrent.org/ticket/3278).
* plymouth-theme-paw-kirigiri - Custom made package containing a plymouth splash I like to use. PKGBUILD can be found [here](https://git.catgirlsin.space/noirscape/bootsplash)
* ffmpeg-compat-57 - Related to building citra-bin on the AUR.
* libsndio-61-compat - Related to building citra-bin on the AUR.

## Adding packages to this repo

This is mostly for my sake. Maintenance is done manually.

Instructions are below for `x86_64`. For `armv7h`, swap out `x86_64` everywhere for `armv7h`

```
git clone https://github.com/noirscape/arch-repo.git /tmp/arch-repo # Clone to temporary repository

cp \<package_tar_file> \<architecture> # move build package over to architecture folder.
cd \<architecture> && repose -vf noirscape

git add -A
git commit -m "Changed repository"
git reset $(git commit-tree HEAD^{tree} -m "Changed repository") # Reset repository back to first commit to reduce disk size
```

## Adding this repository to your Arch install

Add the corresponding line for your architecture to `/etc/pacman.conf`.

x86/i686 packages are not available at this moment in time.

### x86_64

```
[noirscape]
SigLevel = Optional TrustAll
Server = https://raw.githubusercontent.com/noirscape/arch-repo/master/x86_64
```

### armv7h

```
[noirscape]
SigLevel = Optional TrustAll
Server = https://raw.githubusercontent.com/noirscape/arch-repo/master/armv7h
```


## Disclaimer

I am unaffiliated with Arch Linux in any capacity.
