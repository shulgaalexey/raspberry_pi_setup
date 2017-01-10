# raspberry_pi_setup
Raspberry Pi 3 headless setup guidance

## Enable headless SSH
For headless setup, SSH can be enabled by placing a file named 'ssh', without any extension, onto the boot partition of the SD card.
host name  raspberrypi.mshome.net
port 22
open
login pi
password raspberry
https://www.youtube.com/watch?v=uyQ0M1D0iBk

## Headless install using NOOBS image
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

## Remote GUI VNC

http://www.makeuseof.com/tag/run-remote-desktop-raspberry-pi-vnc/
http://mitchtech.net/vnc-setup-on-raspberry-pi-from-ubuntu/

vncserver :1 -geometry 1280x960 -depth 16 -pixelformat rgb565
vncviewer 10.42.0.135:5901

## Temperature of CPU and GPU

https://www.cyberciti.biz/faq/linux-find-out-raspberry-pi-gpu-and-arm-cpu-temperature-command/


## Scan IPs

sudo nmap -sP 192.168.1.0/24     #Scans 192.168.1.0 255.255.255.0

nmap -p 22 --open -sV 192.168.0.*


## Imaginary display

1. Plug in the keyboard and boot the RPi
2. Wait a minute, then type "pi", hit Enter, then "raspberry", and hit enter.
3. Enable SSH with: sudo /etc/init.d/ssh start
4. Type the password "raspberry" again just in case, since it's a sudo command, and hit Enter.

## Win guide
https://www.youtube.com/watch?v=uyQ0M1D0iBk
https://www.youtube.com/watch?v=peZUZo_cSMk&t=34s



## Reference
 * http://qdosmsq.dunbar-it.co.uk/blog/2013/06/noobs-for-raspberry-pi/
 * https://pihw.wordpress.com/guides/direct-network-connection/
