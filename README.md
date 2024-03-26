# arch

## 1 Pre-installation

### 1.1 Acquire an installation image
[Download](https://archlinux.org/download/)

### 1.2 Verify signature

#### [GnuPG](https://wiki.archlinux.org/title/GnuPG)
```
gpg --keyserver-options auto-key-retrieve --verify archlinux-<version>-x86_64.iso.sig
```
#### Arch Linux
```
pacman-key -v archlinux-<version>-x86_64.iso.sig
```

### 1.3 Prepare an installation medium

### 1.4 Boot the live environment

### 1.5 Set the console keyboard layout and font

```
loadkeys sv-latin1
```

### 1.6 Verify the boot mode

### 1.7 Connect to the internet

### 1.8 Update the system clock
```
timedatectl set-timezone Europe/Stockholm
```

### 1.9 Partition the disks

#### 1.9.1 Example layouts

### 1.10 Format the partitions

### 1.11 Mount the file systems

## 2 Installation

### 2.1 Select the mirrors

* ``/etc/pacman.d/mirrorlist``

### 2.2 Install essential packages

```
pacstrap -K /mnt base linux linux-firmware
```

## 3 Configure the system

### 3.1 Fstab

```
genfstab -U /mnt >> /mnt/etc/fstab
```

### 3.2 Chroot

```
arch-chroot /mnt
```

### 3.3 Time

```
ln -sf /usr/share/zoneinfo/Europe/Stockholm /etc/localtime
```

```
hwclock --systohc
```

* systemd-timesyncd (prevent time drift, set up time sync, Network Time Protocol, NTP)

### 3.4 Localization

* ``/etc/locale.gen``
* uncomment en_US.UTF-8 UTF-8
```
locale-gen
```
* ``/etc/locale.conf``
```
LANG=en_US.UTF-8
```
* ``/etc/vconsole.conf``
```
KEYMAP=sv-latin1
```

### 3.5 Network configuration

### 3.6 Initramfs

### 3.7 Root password
```
passwd
```

### 3.8 Boot loader


## Reboot
```
exit
```
```
umount -R /mnt
```
```
reboot
```

## Post-installation

