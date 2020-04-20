---
title: "Areca RAID Controller - Updating Firmware and Passing Password to ArecaCLI / Cli64"
date: "2019-01-10"
categories: linux
---

Verify that cli64 is in your path  
`which cli64`

Firmware Page: https://www.areca.com.tw/support/main.htm

If you do not know the model of your Areca RAID Controller:

```
lspci -vv | grep -C 10 -i areca

```

Example Output:

```
08:00.0 RAID bus controller: Areca Technology Corp. ARC-188x series PCIe 2.0/3.0 to SAS/SATA 6/12Gb RAID Controller (rev 02)
    Subsystem: Areca Technology Corp. ARC-1883 8/12/16/24 Port PCIe 3.0 to SAS/SATA 12Gb RAID Controller

```

This shows that the card in our system is - **ARC-1883**

## Download Firmware

```
# be logged in as root
mkdir ~/raidfw ; cd ~/raidfw
#  this is for Arc-1883 - I obtained it by right clicking the firmware download and selecting `Copy Link Location`
wget http://www.areca.us/support/download/RaidCards/BIOS_Firmware/ARC1883.zip
unzip ARC1883

```

## Update Firmware

```
cli64
 set password=0000
# backs up current config (just in case something breaks)
 sys savebin path=/root/raidfw/areca-arc1883config-2018-10-29.bin
# update in this order
 sys updatefw path=/root/raidfw/ARC1883BIOS.BIN
 sys updatefw path=/root/raidfw/ARC1883BOOT.BIN
 sys updatefw path=/root/raidfw/ARC1883FIRM.BIN
 sys updatefw path=/root/raidfw/ARC1883MBR0.BIN

```
