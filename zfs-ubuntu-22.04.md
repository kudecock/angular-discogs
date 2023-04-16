Step 1: Prepare The Install Environment
---------------------------------------

#. Boot the Ubuntu Server Live CD. From the GRUB boot menu, select *Try or Install Ubuntu*.
   On the *Welcome* page, select your preferred language and enter. On the *Keyboard configuration*, select your keyboard layout and enter.
   On the *Choose type of install* page, select *Help*, enter and select *Enter shell*.

#. Become root::

     sudo -i

#. Setup and update the repositories::

     apt update

#. Install ZFS in the Live CD environment::

     apt install --yes debootstrap gdisk zfs-initramfs

Step 2: Disk Formatting
-----------------------

#. Set a variable with the disk name::

     DISK=/dev/disk/by-id/scsi-SATA_disk1

#. Create bootloader partition(s)::

     sgdisk     -n1:1M:+512M   -t1:EF00 $DISK

