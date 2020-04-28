# The NSWA Ranga Distro Open-source Version

## For lagecy close-source version users

You can follow [this instruction](https://github.com/nswa-project/doc/blob/master/misc/upgrade-from-lagecy-version.md) to upgrade to the open source version

## Fetch all sources

Install Repo Launcher from Google

```
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
```

Fetch sources

```
$ mkdir ranga-workspace
$ cd ranga-workspace
$ repo init -u https://github.com/nswa-project/ranga.git -b master
$ repo sync
```

Setup sources

```
$ cd openwrt
$ ./scripts/feeds update -a
$ ./scripts/feeds install -a
```

Apply ranga's feeds patches

```
$ ../ranga/scripts/apply-feeds-patch.sh
```

## Build

Build ranga

```
$ make menuconfig
```

Choose your device arch, device name. Enable optional OpenWrt/Ranga packages if you wants :-)

Ran make to build

```
$ make
```

Upload and flash your version

```
$ ../ranga/scripts/make_basic_nswafw.sh out/.../xxx.img nswafw.bin
$ ../client/ranga-cli swdeploy -r flash nswafw.bin
```
