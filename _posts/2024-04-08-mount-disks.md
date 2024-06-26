# Mounting Hard Drives

## Steps

### 1. List Disks

``` bash
$ sudo fdisk -l
# SSD
Disk /dev/nvme0n1: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk model: SAMSUNG MZVPV128HDGM-00000              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: EC5B2DFE-A924-466C-B03A-B9458C36DF03
# SDD Partitions
Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048   1050623   1048576   512M EFI System
/dev/nvme0n1p2   1050624 248068095 247017472 117.8G Linux filesystem
/dev/nvme0n1p3 248068096 250068991   2000896   977M Linux swap
# HD1
Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: HGST HTS721010A9
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B2BAE88F-BFE4-11EE-A793-A434D939699D
The backup GPT table is not on the end of the device.
# HD1 Partitions
Device     Start        End    Sectors   Size Type
/dev/sda1   2048 1953523711 1953521664 931.5G Linux filesystem
# HD2
Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: HGST HTS721010A9
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F247758E-BD65-49D7-8EB9-4BD71E6017EA
# HD2 Partitions
Device     Start        End    Sectors   Size Type
/dev/sdb1   2048 1953523711 1953521664 931.5G Linux filesystem
```

### 2. View Partitions

``` bash
# View existing partitions
$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0     4K  1 loop /snap/bare/5
loop... # redacted irrelevant entries
sda           8:0    0 931.5G  0 disk 
sdb           8:16   0 931.5G  0 disk 
sdc           8:32   0   1.8T  0 disk 
└─sdc1        8:33   0   1.8T  0 part /media/blake/Extreme SSD
sr0          11:0    1  37.8G  0 rom  /media/blake/HP4
nvme0n1     259:0    0 119.2G  0 disk 
├─nvme0n1p1 259:1    0   512M  0 part /boot/efi
├─nvme0n1p2 259:2    0 117.8G  0 part /var/snap/firefox/common/host-hunspell
│                                     /
└─nvme0n1p3 259:3    0   977M  0 part [SWAP]
```

### 3. Partition Disks

``` bash
# Open fdisk console for first target disk
$ fdisk /dev/sda
Welcome to fdisk (util-linux 2.38.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.
Command (m for help): n
Partition number (1-128, default 1): <select enter; use default>
First sector (34-1953525134, default 2048): <select enter; use default>
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-1953525134, default 1953523711): <select enter; use default>

Created a new partition 1 of type 'Linux filesystem' and of size 931.5 GiB.
# Repeat steps for /dev/sdb
```

### 4. Format Partitions

``` bash
# Format /dev/sda1 to ext4
$ sudo mkfs.ext4 /dev/sda1
mke2fs 1.47.0 (5-Feb-2023)
Creating filesystem with 244190208 4k blocks and 61054976 inodes
Filesystem UUID: a8f55758-aaec-47a5-8013-43887039f241
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848
Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done  
# Format /dev/sdb1 to ext4
$ sudo mkfs.ext4 /dev/sdb1
mke2fs 1.47.0 (5-Feb-2023)
Creating filesystem with 244190208 4k blocks and 61054976 inodes
Filesystem UUID: 652c6b29-bf98-4521-8f57-100296fc27e6
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848
Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done  
```

### 5. Mount Disks

``` bash
# Make directories
$ sudo mkdir /mnt/sda
$ sudo mkdir /mnt/sdb
# Own directories
$ sudo chown $USER:$USER /mnt/sda
$ sudo chown $USER:$USER /mnt/sdb
# Mount disk partitions
$ sudo mount /dev/sda1 /mnt/sda
$ sudo mount /dev/sdb1 /mnt/sdb
# Validate mount points
$ lsblk /dev/sda
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 931.5G  0 disk 
└─sda1   8:1    0 931.5G  0 part /mnt/sda
$ lsblk /dev/sdb
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sdb      8:16   0 931.5G  0 disk 
└─sdb1   8:17   0 931.5G  0 part /mnt/sdb
```

### 6. Update Filesystem Table

``` bash
# List UUIDs
$ sudo blkid
# Edited output for readability
/dev/nvme0n1p3: UUID="12dc8e82-a72b-4435-a47c-fb717a35d5c3" TYPE="swap" PARTUUID="ca67016a-627d-4cfb-a7c3-40fbdf02a106"
/dev/nvme0n1p1: UUID="47CC-E4E3" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="f4bf8969-b425-46c0-911d-6446f407ee7a"
/dev/nvme0n1p2: UUID="a8f830e4-5c95-4b95-9df2-cc5b5c764ca2" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="07705756-c3e1-43a1-9fa5-c77c3fa846c6"
# New internal HDD
/dev/sda1: UUID="652c6b29-bf98-4521-8f57-100296fc27e6" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="9ba69879-0edc-1846-86f3-9e5ecfcf4b0a"
# New internal HDD
/dev/sdb1: UUID="a8f55758-aaec-47a5-8013-43887039f241" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="db76bd75-1aae-8d41-8762-68d378264cd7"
# External SSD
/dev/sdc1: LABEL="Extreme SSD" UUID="CC37-91A7" BLOCK_SIZE="512" TYPE="exfat" PARTLABEL="Extreme SSD" PARTUUID="4923e12d-bc1b-4a67-b4d4-f6ec3971fa59"
# External disk drive
/dev/sr0: UUID="8c9c95a0f804ac12" LABEL="HP5_PHOENIX" BLOCK_SIZE="2048" TYPE="udf"
# Write changes to /etc/fstab using vim or another text editor (may required sudo)
> # systemd generates mount units based on this file, see systemd.mount(5).
> # Please run 'systemctl daemon-reload' after making changes here.
> #
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
> # / was on /dev/nvme0n1p2 during installation
> UUID=a8f830e4-5c95-4b95-9df2-cc5b5c764ca2 / ext4 errors=remount-ro 0 1
> # /boot/efi was on /dev/nvme0n1p1 during installation
> UUID=47CC-E4E3 /boot/efi vfat umask=0077 0 1
> # swap was on /dev/nvme0n1p3 during installation
> UUID=12dc8e82-a72b-4435-a47c-fb717a35d5c3 none swap sw 0 0
> # manual entry for /dev/sda
> UUID=a8f55758-aaec-47a5-8013-43887039f241 /mnt/sda ext4 rw 0 0
> # manual entry for /dev/sdb
> UUID=652c6b29-bf98-4521-8f57-100296fc27e6 /mnt/sdb ext4 rw 0 0
$ systemctl daemon-reload
# Restart machine
```

### 8. Bookmark Mount Points 

1. Open OS file explorer
2. Select base filesystem (equivalent to `/` working directory)
	- For Debian, select "+ Other Locations" and select "Debian GNU/Linux" drive
3. Select `mnt` directory
4. Select `sda` directory and then select ellipses in navigation bar to add to bookmarks
5. Repeat for `mnt/sdb` (or whatever you named your mount point directories)

## Reference

- [File system types](https://www.networkworld.com/article/972445/how-to-determine-your-linux-system-s-filesystem-types.html)
- [How to partition and format disks](https://www.cherryservers.com/blog/how-to-partition-and-format-disk-drives-on-linux)
- [How to mount disk](https://www.malibal.com/guides/how-to-mount-a-hard-drive-on-linux/)
- [How to mount disk](https://unix.stackexchange.com/questions/72125/correct-way-to-mount-a-hard-drive)
- [Update mount point permissions](https://askubuntu.com/questions/1157165/cant-write-to-mounted-ext4-hard-drive-in-ubuntu-18-04)
- [Introduction to filesystem table](https://www.redhat.com/sysadmin/etc-fstab)
- [Add mount points to explorer bookmarks](https://askubuntu.com/questions/902890/newly-mounted-hard-drive-does-not-show-up-in-file-manager)
