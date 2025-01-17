# Penetration Testing Strata Scripts for Bedrock Linux

## About the Scripts
These scripts can build a [Kali Linux](https://www.kali.org/) stratum and/or a [BlackArch](https://blackarch.org/index.html) stratum on [Bedrock Linux](https://bedrocklinux.org/). For Kali Linux, the script fetches a live Kali Linux image (currently version 2020.4) and uses `unsquashfs` to copy the relevant files to `/bedrock/strata/kali`. For BlackArch, the script it downloads a fresh Arch Linux strata to `/bedrock/strata/blackarch`, then installs the BlackArch repository ontop of it.

## Requirements
The following are the system requirements for this script:
* Bedrock Linux installed
* x64 system
* Sufficent disk space to download and unpack:
  * a Kali Linux ISO file for the Kali Linux script; or
  * a new Arch Linux stratum for the BlackArch script.

In addition to the above system requrements, the scripts require that the following packages are available on your system:
* For the Kali Linux script:
  * wget
  * unsquashfs
* For the BlackArch script:
  * wget

## Running the Scripts
You can download the scripts using the following command by cloning this repo

### Building a Kali Linux Stratum
Make the Kali Linux script executable:
```
cd ./kali-linux-on-Bedrock
chmod +x build-kali.sh
```
Run the script as root:
```
sudo ./build-kali.sh
```
### Building a BlackArch Stratum
Make the BlackArch script executable:
```
cd ./kali-linux-on-Bedrock
chmod +x build-blackarch.sh
```
Run the script as root:
```
sudo ./build-blackarch.sh
```
You can now install all of the BlackArch packages with the following command:
```
sudo strat -r blackarch pacman -S blackarch
```
`pacman` will ask you about a number of dependencies, which you can address by pressing enter for each dependency it asks about, and answering `y` when it asks you the following question:
```
Do you want to skip the above packages for this upgrade? [y/N]
```
Note, you may run into errors when installing `blackarch` where `pacman` complains that `blackarch-mirrorlist: /etc/pacman.d/blackarch-mirrorlist exists in filesystem`. You can get around this by running the following command to install `blackarch`:
```
sudo strat -r blackarch pacman -S blackarch --overwrite '*'
```
This appears to be an upstream bug with BlackArch and is not (as far as I can tell) related to this script.

## Note About Testing and Errors
It is very possible that these scripts can destroy your system, delete your data, or set your cat on fire. Please be careful. I recommend testing this out in a virtual machine and/or executing each command manually and monitoring any output.

Please note that these scripts have only been (minimally) tested on a hijacked Ubuntu installation. It is possible that you may have to adjust the shebang at the beginning of each script depending on the location of bash on your system, which you can determine by running `which bash`. Creating a Kali Linux stratum and a BlackArch stratum are buggy processes. When you update and upgrade packages, you may receive some errors, but for the most part, the packages should be usable.

## About Bedrock Linux
Please note that these scripts are not affiliated with Bedrock Linux.

[Bedrock Linux](https://bedrocklinux.org/) is an extremely cool project that allows you to use packages from multiple Linux distributions at the same time. If you are not familiar with it, I highly recommend checking it out. From the Bedrock Linux website:

> Bedrock Linux is a meta Linux distribution which allows users to mix-and-match components from other, typically incompatible distributions. Bedrock integrates these components into one largely cohesive system.
>
> For example, one could have:
>
> * Debian's stable coreutils
> * Arch's cutting edge kernel
> * Void's runit init system
> * A pdf reader with custom patches automatically maintained by Gentoo's portage
> * A font from Arch's AUR
> * Games running against Ubuntu's libraries
> * Business software running against CentOS's libraries
>
> All at the same time and working together mostly as though they were packaged for the same distribution.
