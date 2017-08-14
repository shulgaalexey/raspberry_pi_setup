Raspberry PI 3 headless setup on Tizen
======================================

Source: https://github.com/Samsung/iotjs/blob/master/docs/build/Build-for-RPi3-Tizen.md


Remote terminal wia Serial port
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

```
User id/passwd : root / tizen
(target)$ ifconfig eth0 down
(target)$ ifconfig eth0 192.168.1.11 netmask 255.255.255.0 up
(target)$ route add default gw 192.168.1.1
```


## Reference
 * https://github.com/Samsung/iotjs/blob/master/docs/build/Build-for-RPi3-Tizen.md
 * https://wiki.tizen.org/Raspberry_Pi#Debugging
