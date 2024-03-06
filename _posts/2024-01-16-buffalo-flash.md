# Research

## Forum

[MakeMKV Flash Guide](https://forum.makemkv.com/forum/viewtopic.php?f=16&t=19634)
[SDFtool Flasher](https://forum.makemkv.com/forum/viewtopic.php?f=16&t=22896)

## Posts

[Re: Ultimate UHD Drives Flashing Guide Updated 2023 - Confirming Steps for BRUHD-PU3-BK](https://forum.makemkv.com/forum/viewtopic.php?p=147135#p147135)

[BRUHD-PU3-PK BU12 to BU10?](https://forum.makemkv.com/forum/viewtopic.php?p=98648#p98648)

1. HL-DT-ST-BD-RE_BU40N-BU12-OM01001-211902230922.bin
2. DE_Buffalo_BRUHD-PU3_BU10 OR DE_LG_BU40N_1.00

[Re: SDFtool Flasher](https://forum.makemkv.com/forum/viewtopic.php?p=146552#p146552)

> BU40N 1.03-MK is the firmware to flash to first. If you want to flash another after that, such as BU40N 1.00 (for more software compatibility) you can.

## Documentation

1. [Choose disk drive](https://forum.makemkv.com/forum/viewtopic.php?f=16&t=19634)
2. [Download MakeMKV program](https://www.makemkv.com/download/)
3. [Download SDFtool Flasher](https://forum.makemkv.com/forum/viewtopic.php?f=16&t=22896)
4. [Download "All You Need Firmware Pack"](https://forum.makemkv.com/forum/viewtopic.php?f=16&t=22896)
5. Configure SDFtool Flasher
   - Select optical drive path
   - Confirm `MT1595 Platform` and `Encrypted Firmware`; leave boot loader unselected
   - Select "WRITE Firmware"
   - Select firmware to be written: ``; [TBD]
   - Select "START" and wait for completion

## Original Specs

``` plaintext
Drive Information
OS device name: E:
Manufacturer: BUFFALO
Product: Optical Drive
Revision: BU14
Serial number: MO2N5DA3110
Firmware date: 2121-06-21 13:30
Bus encryption flags: 1F

LibreDrive Information
Status: Possible, not yet enabled
Drive platform: MT1959
```

## New Specs

``` plaintext
Drive Information
OS device name: E:
Manufacturer: BUFFALO
Product: Optical Drive
Revision: 1.03
Serial number: MO2N5DA3110
Firmware date: 2118-10-24 19:34
Bus encryption flags: 17

LibreDrive Information
Status: Enabled
Drive platform: MT1959
Firmware type: Patched (microcode access re-enabled)
Firmware version: 1.03
DVD all regions: Yes
BD raw data read: Yes
BD raw metadata read: Yes
Unrestricted read speed: Yes
```
