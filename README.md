### Sesja Linuksowa 2017 - Workshops

http://14.sesja.linuksowa.pl/pl

## Getting Started

These instructions will help you setup workspace on your build host machine for development during workshops!

### Prerequisites

Prepare approximately 30 GB of size on your build host machine, Yocto during build image require fetch all dependencies and require sources.

[System dependencies](http://www.yoctoproject.org/docs/2.2.1/ref-manual/ref-manual.html#required-packages-for-the-host-development-system)

*In case of lack of supported distribution on your build host install 'Ubuntu' on 'Virtual-Box'*

### Installing

Prepare workspace:
```
mkdir sesja-linuksowa-workspace
cd sesja-linuksowa-workspace/
```

Download repo tool:
```
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

Initialize wporkspace using repo tool:
```
repo init -u https://github.com/lukaszgard/sesja-manifest.git
repo sync
```

Setup build-enviroment to build:
```
cd yocto-build/
source oe-init-build-env rpi-build
```

Add meta-raspberrypi layer into conf/bblayers.conf file:
```
BBLAYERS ?= " \
  /home/user/yocto-build/meta \
  /home/user/yocto-build/meta-poky \
  /home/user/yocto-build/meta-yocto-bsp \
  /home/user/yocto-build/meta-raspberrypi \
  "
```

Setup Raspberry version in order to build proper image:
```
echo 'MACHINE = "raspberrypi3"' >> conf/local.conf
```

Build image:
```
bitbake rpi-hwup-image
```


### Help links 

* [Yocto Project Quick Start](http://www.yoctoproject.org/docs/2.2.1/yocto-project-qs/yocto-project-qs.html#yocto-project-qs-intro) - Quick overwiew on Yocto.
* [Using Repo](https://source.android.com/source/using-repo) - Repo tool command reference.
* [Meta RaspberryPi](http://git.yoctoproject.org/cgit.cgi/meta-raspberrypi/tree/README) - RaspberryPi configuration image.
