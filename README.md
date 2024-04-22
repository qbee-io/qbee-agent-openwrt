# qbee-agent-openwrt
qbee-agent package for OpenWRT

## Build Guide

- Prepare the build environment as described [here](https://openwrt.org/docs/guide-developer/toolchain/install-buildsystem)

- Install a recent version of the Go programming language from [here](https://go.dev/doc/install) and make sure you have `go` in the system path.

- Download the SDK relevant to the OpenWRT version, target and subtarget from [here](https://archive.openwrt.org/releases)

- In the untar'ed SDK directory, fetch this repo and build the qbee-agent package

```sh

git clone https://github.com/qbee-io/qbee-agent-openwrt package/qbee-agent
./scripts/feeds update packages
make defconfig
make package/qbee-agent/compile
```

- Package is available in the `bin/packages` file structure

```sh
find bin/packages/ -name "qbee-agent*.ipk"
```
