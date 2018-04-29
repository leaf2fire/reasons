# Installing Arch Linux for Personal Use

A short guide to installing Arch Linux for the average Linux user.

Example system details

* [BIOS](https://en.wikipedia.org/wiki/BIOS)/GPT
* CPU: Intel
* Bootloader: [GRUB](https://wiki.archlinux.org/index.php/GRUB)
* Internet connection: wifi

Parts

* Part 0: Boot Arch Linux from USB
* Part 1: Set up partitions
* Part 2: Install base packages
* Part 3: Post install



## Part 0: Boot Arch Linux from USB

1. [Download the ISO](https://www.archlinux.org/download/)
2. [Download Rufus](https://rufus.akeo.ie/)
3. [Use Rufus to create bootable USB](https://wiki.archlinux.org/index.php/USB_flash_installation_media#Using_Rufus)
4. Set target computer to boot from USB or external devices. There should be an
option to do this in the **boot menu**.
5. Insert USB with Arch into target computer.
6. On next startup, target computer should boot Arch from USB. (Restart target
computer.)
7. Select Boot Arch Linux.

*Note*: Rufus is only available for Windows. [Alternative methods for bootable
USB creation](https://wiki.archlinux.org/index.php/USB_flash_installation_media).

*Note*: [Alternate non-USB methods](https://wiki.archlinux.org/index.php/Category:Getting_and_installing_Arch).



## Part 1: Set up partitions

*Warning*: You're committed to installing Arch from here on. There is no going 
back.

We'll be creating two partitions: one for the bootloader, GRUB, and
one for the root directory.

1. Identify the disk to install Arch on with `fdisk -l`.
2. Suppose we want to install Arch on `/dev/sda`. Enter `fdisk /dev/sda` to edit 
partitions.
3. Enter `g` to create new empty GPT partition table.
4. Enter `n` to make the partition for GRUB.
    * Select default for partition number and first sector.
    * Enter `+1M` for last sector.
    * Change partition type by entering `t` then `4` for BIOS boot.
5. Enter `n` to make the partition for the root directory.
    * Select default for all.
6. Make the partitions for real with `w`.
7. Enter `mkfs.ext4 /dev/sda2` to format the root partition.
8. Enter `mount /dev/sda2 /mnt` to mount the root directory.

*Note*: More on [partitioning](https://wiki.archlinux.org/index.php/Partitioning). More on [fdisk](https://wiki.archlinux.org/index.php/Fdisk).



## Part 2: Install base packages

1. Connect to the internet with `wifi-menu`.
2. Update the system clock with `timedatectl set-ntp true`.
3. Install [base](https://www.archlinux.org/groups/x86_64/base/) with 
`pacstrap /mnt base`.

## Part 3: Post install

## Automount

`genfstab -U /mnt >> /mnt/etc/fstab`

## Chroot

`arch-chroot /mnt`

## Intel microcode updates

`pacman -S intel-ucode`

## GRUB

1. `pacman -S grub`
2. `grub-install --target=i386-pc /dev/sda`
3. `grub-mkconfig -o /boot/grub/grub.cfg`

## Locale Settings

1. `ln -sf /usr/share/zoneinfo/America/New_York /etc/localtime`
2. `hwclock --systohc`
3. Uncomment en_US.UTF-8 UTF-8 and other needed localizations in 
`/etc/locale.gen` and run `locale-gen`.
4. Write `LANG=en_US.UTF-8` in `/etc/locale.conf`.

*Note*: You can edit files with `nano` or `vim`.

## Wifi

1. `pacman -S iw wpa_supplicant dialog`
2. `wifi-menu -o`

*Note*: See [netctl](https://wiki.archlinux.org/index.php/Netctl) for more info.

*Troubleshoot*: Wifi not working?

1. Find profile `netctl list`
2. Check status `netctl status profile`
3. Reconnect `netctl restart profile`

## Hosts

Set hostname in `/etc/hostname`.

In `etc/hosts`, write the following three lines. Replace hostname with the name
set in `/etc/hostname`.

`127.0.0.1 localhost`
`::1       localhost`
`127.0.0.1 hostname.localdomain hostname`

## User

1. `pacman -S sudo`.
2. Set password for root `passwd`.
3. `useradd -m USER_NAME`
4. `passwd USER_NAME`
5. Add `USER_NAME ALL=(ALL) ALL` to `/etc/sudoers`.

## Reboot

That's pretty much it. 

*Note*: USB stick no longer needed.