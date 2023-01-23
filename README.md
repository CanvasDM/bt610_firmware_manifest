# BT610 Firmware Manifest Repo

This manifest repo will pull all the required firmware for the Sentrius BT610 sensor.

> **NOTE:** Customization process is required to enable all features of Laird Connectivity provided Canvas Device Management platform. Please [contact Laird Connectivity](https://www.lairdconnect.com/contact) if you require Canvas Device Management Services before you start development.

## Required Hardware

To program and/or debug the BT610 the following is required:

- [Laird Connectivity USB-SWD Programmer](https://www.lairdconnect.com/wireless-modules/programming-kits/usb-swd-programming-kit)

## Cloning Firmware

> **WARNING:** On Windows do not clone into a starting folder path longer than 12 characters or else the firmware will not build.

This is a Zephyr `west` manifest repository. To learn more about `west` see [here](https://docs.zephyrproject.org/latest/guides/west/index.html).

To clone this repository properly use the `west` tool. To install `west` you will first need Python3.

Install `west` using `pip3`:

```
pip3 install --user -U west
```

Once `west` is installed, clone this repository using `west init` and `west update`:

```
# Checkout the latest manifest on main
west init -m https://github.com/CanvasDM/bt610_firmware_manifest.git --mr main

# Checkout the latest manifest on GA1
west init -m https://github.com/CanvasDM/bt610_firmware_manifest.git --mr GA1

# Checkout a specific version
west init -m https://github.com/CanvasDM/bt610_firmware_manifest.git --mr v1.0.0

# Now, pull all the source described in the manifest
west update
```

## Preparing to Build

If this is your first time working with a Zephyr project on your computer you should follow the [Zephyr getting started guide](https://docs.zephyrproject.org/latest/getting_started/index.html#) to install all the tools.

v0.14.2 of the Zephyr SDK is recommended for building the firmware.

## Building the Firmware

> **WARNING:** Before building the firmware, be sure to install all python dependencies

From the directory where you ran `west update`, issue the following command:

```
# Linux, macOS and Windows
pip3 install --user -r zephyr/scripts/requirements.txt
pip3 install --user -r nrf/scripts/requirements.txt
pip3 install --user -r modules/lib/laird_connect/attributes/generator/requirements.txt
```

Then build the firmware

```
west build -p auto -b bt610 -d bt610_firmware/build bt610_firmware

```

### Secure Sign Firmware

In order to build a secure image there are extra options that need to be used when building the firmware.

The following command will use test keys in the repo to show how to build a secure image.

```
# Linux, macOS

TODO

# Windows

TODO
```
