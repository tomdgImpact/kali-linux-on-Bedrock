# Kali Linux Stratum Builder for Bedrock Linux

## About the Script
This script will build a Kali Linux stratum on [Bedrock Linux](https://bedrocklinux.org/). It does so by fetching a live Kali Linux image (currently version 2020.3) and using `unsquashfs` to copy the relevant files to `/bedrock/strata/kali`.

## Requirements
The following are the system requirements for this script:
* Bedrock Linux installed
* x64 system
* Sufficent disk space to download and unpack a Kali Linux ISO file

In addition to the above system requrements, the script requires that the following packages are available on your system:
* wget
* unsquashfs

## Running the Script
You can download the script using the following command:
```
git clone https://github.com/nexxius/Bedrock-Linux-Kali-Stratum-Builder
```
Make the script executable:
```
cd ./Bedrock-Linux-Kali-Stratum-Builder
chmod +x buildkali.sh
```
Run the script as root:
```
sudo ./buildkali.sh
```

## Note About Testing and Errors
It is very possible that this script can destroy your system, delete your data, or set your cat on fire. Please be careful. I recommend testing this out in a virtual machine and/or executing each command manually and monitoring any output.

Please note that this script has only been (minimally) tested on a hijacked Ubuntu installation. This should work assuming you have Ubuntu (or maybe Debian) installed as a stratum, but it is possible that you may have to adjust the shebang depending on the location of bash, which you can determine by running `which bash`. Creating a Kali stratum is still a buggy process and when you update and upgrade the packages, you may receive some errors (but for the most part, the packages should be usable).

## About Bedrock Linux
Please note that this script is not affiliated with Bedrock Linux.

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
