# qbee-agent-openwrt
qbee-agent package for OpenWRT

## Build Guide

- Set up the OpenWRT SDK as described here [here](https://openwrt.org/docs/guide-developer/toolchain/use-buildsystem)

- In SDK directory, download Makefiles with git:

```sh
git clone https://github.com/qbee-io/qbee-agent-openwrt package/qbee-agent
```

```sh
./scripts/feeds update -a
./scripts/feeds install -a

# Make sure to select the qbee-agent package for target under Administration
make menuconfig

make tools/install
make toolchain/install

make defconfig # or make menuconfig

make package/qbee-agent/{clean,compile} V=s
```
