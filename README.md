# raspberry_pi_setup
Raspberry Pi 3 headless setup guidance

## OS Image on SD. NOOBS
0. Insert and unmount SD card
1. Setup SD card partitions: sudo fdisk /dev/mmcblk0
2. Delete all partitions (command d)
3. Create new partition (command n)
  * partition type: p
  * partition number: 1
  * first sector: 2048
  * last sector: default
4. Change file system (command t, type b)
5. Write changes (command w)
6. Format SD card: sudo mkfs.vfat /dev/mmcblk0p1
7. Download OS image:  http://www.raspberrypi.org/downloads
   sha1sum NOOBS_v2_x_xx.zip for ensure
8. Mount SD card and unzip image
   unzip ~/Downloads/NOOBS_v2_x_xx.zip
9. Switch to headless OS install: append to recovery.cmdline file a line
   silentinstall runinstaller quiet ramdisk_size=32768 root=/dev/ram0 init=/init vt.cur_default=1 elevator=deadline
10. Unmount and unplug SD card
11. Insert SD card into RPi, connect network cable, RPi power on
12. Wait for 40~60 min, watch RPi activity LED
13. Check RPi ip: 
    * arp -a
    * ip neighbor list
14. ssh pi@rpi_ip_addr

