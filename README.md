# Realtek r8126 DKMS

![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/wjz304/realtek-r8126-dkms?sort=semver&style=for-the-badge)

This provides Realtek r8126 driver in DKMS way so that you can keep the latest driver even after the kernel upgrade.

## Before use

This DKMS package is for Realtek RTL8126 (r8126 in module name) Ethernet, which is designed for the PCI interface.

If you are searching for the Realtek 2.5 Gbits **USB Ethernet**, which may use RTL8156 (r8152 in module name), you are in the wrong place. Please refer to another DKMS project for that Realtek driver.

- [Realtek R8152 DKMS](https://github.com/wjz304/realtek-r8152-dkms)

## Installation

There are 3 ways to install this DKMS module. Choose one as your tastes.

Those are not interfering with each other. So you can do all 3 methods but absolutely you don't need to.

Installation using the Debian package is recommended for the sake of getting the newer driver.

### Debian package

#### Released package file

Download the latest Debian package from the Release tab on the Github repository.

Then enter the following command.

```bash
sudo dpkg -i realtek-r8126-dkms*.deb
```

> If multiple files selected by the wild card, you should type the specific version of the file.
>
> ```bash
> sudo dpkg -i realtek-r8126-dkms_*_amd64.deb
> ```

If dependency error occurs, try to fix that with `apt` command.

```bash
sudo apt install --fix-broken
```

### autorun.sh

Using the `autorun.sh` script that Realtek provides on their original driver package. This is **not installed as a DKMS**, only efforts to the current kernel.

Download or clone this repository and move to the extracted directory, then run the script.

```bash
sudo ./autorun.sh
```

### dkms-install.sh

This script is from aircrack-ng team. You can install the DKMS module by a simple command.

Download or clone this repository and move to the extracted directory, then run the script.

```bash
sudo ./dkms-install.sh
```

## Debian package build

You can build yourself this after installing some dependencies including `dkms`.

```bash
sudo apt install devscripts debmake debhelper build-essential dkms
```

```bash
dpkg-buildpackage -b -rfakeroot -us -uc
```

## LICENSE

GPL-2 on Realtek driver and the debian packaing.

## References

- [Realtek r8126 driver release page](https://www.realtek.com/Download/List?cate_id=584)
- [awesometic's realtek-r8125-dkms, where got hint from](https://github.com/awesometic/realtek-r8125-dkms)
