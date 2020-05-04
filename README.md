# The NSWA Ranga Distro Open-source Version

## For lagecy close-source version users

You can follow [this instruction](https://nswa-project.github.io/upgrade-to-opensource-version.html) to upgrade to the open source version

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

If you are using NSWA Ranga system, make a nswafw format update bundle and upload to flash your version

```
$ ../ranga/fw/make_fullpack_fw.sh out/.../xxx.img nswafw.bin
$ ../client/ranga-cli swdeploy -r flash nswafw.bin
```

If you are using generic OpenWrt distro, install by SSH

```
$ scp out/.../xxx.img root@192.168.1.1:/tmp
$ ssh root@192.168.1.1
OpenWrt # cd /tmp
OpenWrt /tmp# sysupgrade -n xxx.img
```

If you are using another system or stock system, use device-specific methods, for example, flash in u-boot console by UART TTL
