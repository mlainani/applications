# Create a sample package for OpenWRT

Assuming you've clone the OpenWRT repo locally and build the whole system a given target

```
cd path/to/openwrt
echo src-link applications /home/kong/making/applications >> feeds.conf.default
./scripts/feeds update applications
./scripts/feeds search hello
./scripts/feeds install -f helloworld
make menuconfig
make package/helloworld/compile
tree bin/packages/
```