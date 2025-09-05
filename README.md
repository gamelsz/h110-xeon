# Xeonlake 1151 Guide

⚠️ **I'm not responsible for any device damage caused by mindlessly following this guide**

Guide was tested on H110 chipset motherboard. It's not guaranteed to work on other chipsets.

## What is it?
This repo will lead you through modifying your [Skylake](https://en.wikipedia.org/wiki/Skylake_(microarchitecture)) (Intel 6th gen) motherboard BIOS to be able to run CPU's up to [Coffee Lake R](https://en.wikipedia.org/wiki/Coffee_Lake#List_of_9th_generation_Coffee_Lake_processors_(Coffee_Lake_Refresh)) (Intel 9th gen)

It will also enable support for Intel Xeon CPU's. Specifficaly E3 series based on the same socket (LGA1151).

8th/9th gen are expected to work with DDR3 RAM (officially supported up to 7th gen) but it's not confirmed yet. It will get clarified as soon as I get my hands on one of the completely DDR4 CPU's.

## What do I need?
1. First of all - a motherboard. Your safest option is something with H110 chipset. It may be harder to execute (or even impossible) on more advanced motherboards. So, choose H110. I was making everything on [this Gigabyte board](https://www.gigabyte.com/Motherboard/GA-H110M-DS2-DDR3-rev-10#ov) althrough, it's also safe to use DDR4 standard boards. By default you won't be able to use CPU's newer than [Kaby Lake](https://en.wikipedia.org/wiki/Kaby_Lake)
2. CoffeeTime software with v0.99 executable - this one is the easiest options in case of modifying your BIOS. If you want to go more avantgarde look up to Intel CSME tools to edit the ME Region. You can find the CoffeeTime on the internet. I can't provide it here because of copyrights :(
3. BIOS for your model of motherboard. In this case I used F20f (Mar 09, 2018) version but you should be fine with anyone.
4. A thumbdrive formated to FAT32, it can even be 1GB. We will use it only to store BIOS.
5. [FOR GIGABYTE MOTHERBOARDS] Any hex editor. I used [HXD](https://mh-nexus.de/downloads/HxDSetup.zip) for instance.
6. **[OPTIONAL]** CH341A clip with module/soldering iron with module to reprogram the BIOS if update didn't succeed.

## Step by step
1. Load your BIOS into CoffeeTime and check if the versions, models and dates are written correctly.
2. First of all you have to change the ME Region. In my case I'm going to use Xeon E3 1270v5 so I choose 11.8.77 Corporate. You should be fine with it either when using consumer processors.
3. After replacing the ME Region it's time to disable ME.
4. After disabling it's time to use every patch mentioned in the General tab.
5. [FOR MSI MOTHERBOARDS] Navigate to Extra and disable ME warning. If you're not using MSI motherboard, skip this step
6. Update the VBIOS and GOP to the newest version possible.
7. [FOR CONFIDENTIAL/MOBILE UNITS] You have to use the microcode tab for your unit.
8. Save your new bios with the SAME EXACT extension you downloaded it. It's also recommended to use the same name.
9. [FOR GIGABYTE MOTHERBOARDS] Load your brand new BIOS into hex editor and search for **$BDR**. Locate the BIOS integrity verification bit and change it to 00 to disable it.
10. Save your BIOS and upload it into FAT32 thumbdrive
11. Run your PC and use built-in BIOS updater. If PC didn't boot you have to desolder the BIOS chip from the motherboard and force program BIOS into it. You can also use a clip with tapes instead of soldering iron/hotair. Remember to make a copy of your working BIOS! 
12. If BIOS update succeed, you can now prepare your CPU. If it's a CPU up to 8th gen, you don't have to do pin mod and you can run it out of the box. You have to do pin mod in all Coffee Lake CPU's. Pin work is provided below, it's differed by the motherboard manufacturer.

## Known issues
1. Intel Xeon E3 v5 are known of incorrect temperature measurements on H110 chipset.

## Credits
- BSV Services
- Arijit Guha
