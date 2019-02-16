---
layout: post
title: 树莓派wifi模块No-wireless-interface-found-解决方法
category: 技术
tags: [树莓派]
keywords: 树莓派
---


## 解决步骤

Solution that worked for me:
After hours of Googling, I am still not sure how exactly I solved the problem but it suddenly work. This is what I did step by step:

Change whatever in /etc/wpa_supplicant/wpa_supplicant.conf to:
1
2
3
4
5
6
7
8
#ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
#update_config=1
#country=MR
 
network={
ssid="Students"
psk="mypass"
}
Change whatever in /etc/network/interfaces to
1
2
3
4
5
6
7
8
9
10
11
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet manual
 
allow-hotplug wlan0
iface wlan0 inet manual
Shutdown pi
Plug a working external wifi USB device
Boot pi
Here none of the 2 Wifi device should work. I tested to connect to the internet using an Ethernet cable and the LAN connection still works fine.
Unplug Ethernet cable.
Now whatever in /etc/wpa_supplicant/wpa_supplicant.conf to:
1
2
3
4
5
6
7
8
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=MR
 
network={
ssid="Students"
psk="mypass"
}
Reboot pi

[参考地址](https://tolotra.com/2018/07/22/how-to-solve-no-wireless-interface-found-on-a-raspberry-pi-3/)


