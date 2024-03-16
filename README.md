# Simple publish-subscribe protocol (OpenWrt)

SPSP connects low power IoT clients to MQTT or other protocols.

It's an extensible framework for publish-subscribe pattern.

Main goal is to create highly reliable platform for message delivery from and
to IoT devices while taking into account protocol-specific, performance and
power restrictions.

This is SPSP's OpenWrt feed.

## Usage

To build the packages, download and unpack
[OpenWrt SDK](https://openwrt.org/docs/guide-developer/toolchain/using_the_sdk)
for your device's platform.

Prepend to `feeds.conf.default`:

```
src-git spsp https://github.com/DavidB137/spsp-openwrt.git;main
```

Run:

```sh
./scripts/feeds update -a
./scripts/feeds install -a
make package/spsp/compile
```

Built packages will be located in `bin/packages/<TARGET>/spsp` directory.

## Packages

There are currently 3 packages provided:

- **`libspsp`**: Shared library of SPSP.
- **`spsp-bridge-espnow`**: ESP-NOW SPSP bridge. Uses `libspsp`.
- **`libpaho-mqtt3as`**: Paho MQTT C library for MQTT communication.

Configuration of SPSP packages is through unified UCI config files.
