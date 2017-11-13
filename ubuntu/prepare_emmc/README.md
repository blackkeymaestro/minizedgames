By: Eddie Vergara
eavergara@gmail.com

Instructions for Installing Ubuntu Filesystem on Minized eMMC 

The Minized ships with a single FAT32 partition in the eMMC.  In order
to install the Ubuntu filesystem, we need to format the eMMC such that 
there are two partitions: boot (DOS) and root (EXT4)

A. Prepare USB Stick with the following conditions
  1. USB fully formatted for EXT4.  
  2. USB files in the following directory structure

  /
  prepare_emmc.sh 
    /boot (in tar ball)
      image.ub
      wpa_supplicant.conf

    /ext4 (in tar ball)
      /lib
        (ext4 libs)
      mkfs.ext4
  
    /rootfs (Download https://rcn-ee.com/rootfs/eewiki/minfs/ubuntu-16.04.3-minimal-armhf-2017-10-10.tar.xz) 
      armhf-rootfs-ubuntu-xenial.tar (extract from ubuntu-16.04.3-minimal-armhf-2017-10-10.tar.xz)

B)Boot Minized with built-in image, mount the usb to /mnt/usb/boot/image and run this script
  mount /dev/sda1 /mnt/usb
  /mnt/usb/prepare_emmc.sh
  
prepare_emmc script accomplishes the following
1) Partitions eMMC into one 128M boot partition, and ext4 partition with the rest of the device
2) Formats boot as DOS boot partition; Formats root as EXT4 partition 
3) Copies Linux kernel and wpa_supplicant onto boot partition
4) Uncompresses Ubuntu filesystem onto root partition
5) Sets root permissions to the filesystem


