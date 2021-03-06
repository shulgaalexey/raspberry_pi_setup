Raspberry PI 3 headless setup on Tizen
======================================

Source: https://github.com/Samsung/iotjs/blob/master/docs/build/Build-for-RPi3-Tizen.md

If doownloading of sd fusing script doesn't work, try this link:

```
$ wget https://git.tizen.org/cgit/platform/kernel/linux-rpi3/plain/scripts/sd_fusing_rpi3.sh?h=submit/tizen/20170725.223437 --output-document=sd_fusing_rpi3.sh
```

### Boot & Kernel

http://download.tizen.org/snapshots/tizen/unified/latest/images/standard/iot-boot-arm64-rpi3/

### Platform

http://download.tizen.org/snapshots/tizen/unified/latest/images/standard/iot-headless-2parts-armv7l-rpi3/


Remote terminal via Serial port
-------------------------------

```
sudo screen /dev/ttyUSB0 115200
```

https://wiki.tizen.org/Raspberry_Pi#Debugging


or


```
sudo minicom
```



Setup IP
--------

### On RPi3

```
User id/passwd : root / tizen
(target)$ ifconfig eth0 down
(target)$ ifconfig eth0 192.168.1.11 netmask 255.255.255.0 up
(target)$ route add default gw 192.168.1.1
```

### On Host PC

```
(host)$ sudo ifconfig eth1 down
(host)$ sudo ifconfig eth1 192.168.1.1 netmask 255.255.255.0 up
```

### SDB

```
sdb connect 192.168.1.11
sdb shell
```

Information of connecting to UART
---------------------------------

In case of PL2303:
```
TXD0(08pin) → UART Board RXD
RXD0(10pin) → UART Board TXD
Ground(06pint) → UART Board GND
Set Jumper switch to 3.3V.
```


Reference
---------
 * https://github.com/Samsung/iotjs/blob/master/docs/build/Build-for-RPi3-Tizen.md
 * https://wiki.tizen.org/Raspberry_Pi#Debugging
