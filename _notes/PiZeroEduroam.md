---
layout: post
permalink: /Pi-Eduroam/
title: How to set up Eduroam on a Pi 
date: 2017/03/11
colour: "#080808"
word-color: "#AAAAAA"
link-color: "white"
published: true
---

# {{ page.title }} 

---
{: .thick-rules}


## Contents:

|---
| [Ingredients](#ingredients)			|
| [TL;DR](#tldr)				        |
| [Using wpa_cli](#using-wpa_cli)		|
| [Further Reading](#further-reading)	|
|===
{: .contents-section}

---

## Ingredients:

1 x Power Supply  
1 x Way to see a terminal (Display, Serial connection, SSH over ethernet)  
1 x Pi  
1 x Wifi Antenna (not needed if Pi 3 or Pi Zero W)  

---

## TL;DR:

~~~ bash
sudo wpa_cli   
scan  
scan_results  
add_network   
(read the output from add_network, it will be referred to as n here)  
set_network n ssid "eduroam"  
set_network n scan_ssid 1  
set_network n proto WPA2  
set_network n priority 1   
set_network n key_mgmt WPA-EAP   
set_network n eap PEAP  
set_network n pairwise CCMP  
identity n user@university.domain  
password n pa$$word4aBoVeAcc0unt  
set_network n phase2 "auth=MSCHAPV2"  
select_network n  
(the screen should fill with text about how great it is working)  
save_config  
~~~
 
# Using WPA_CLI

---

For this tutorial we will be using wpa_cli, which is a utility included on Raspbian by default, this is a terminal application, if you want to use a GUI that is out of the scope of this tutorial. 

wpa_cli is an interactive script for setting up wireless networks using the command line. It is a frontend to wpa_supplicant, this means there only needs to be these commands to set it up and no need to go edit config files. 

wpa_cli can also be used to set up other wifi networks other than eduroam.

launch wpa_cli by running the following in the terminal:

~~~ bash
sudo wpa_cli
~~~

## Scanning to see the networks

~~~ bash
scan
scan_results
~~~

using wpa_cli you first let it know that some networks exist, this is the equivolent of turning on the wifi of your computer and looking at the list of the wifi networks your computer can see. You will be able to see a bunch of networks if you are in a populous area. What we want to see is one (or more) called eduroam and then we can proceed. If you can't see eduroam then you probably aren't around a eduroam connected area, if you are then I am sorry but you may need to move around a bit and repeat this until you can see some.

## Adding an empty network

~~~ bash
add_network
~~~

This command will make an empty "profile" for a network, and will print out a number to the console, if this is your first time setting up with wpa_supplicant on this pi it will likely be 0 so for the purposes of this tutorial I will put 0, if it isnt then replace the 0 with whatever number is printed to the screen. 

## Setting up

~~~ bash
set_network 0 ssid "eduroam"
~~~ 

This is somewhat self explanitory set_network allows you to set various values that a network can have, 0 is the network id, ssid is a fancy name for name of network, then you follow it up with "eduroam" as the value for ssid.

~~~ bash
set_network 0 scan_ssid 1 
~~~

Eduroam despite appearing as a single network as you move around in other OSs is actually a collection of networks that all have the same name. This means you can go anywhere in the world and connect with the same credentials, unfortunately as we are setting it up manually we need to tell wpa that it has to scan for ssid to reconnect as we move it. 
 
~~~ bash
set_network 0 scan_ssid 1 
set_network 0 proto WPA2
~~~

When you are using a wifi network most likely it is encrypted between you and the wifi network (wifi is just radio waves and if it wasn't encryptedanyone could just listen into it and see whatever it was you were doing on the network). 
In our case eduroam seems to always be WPA2, which a lot of home networks are. And if fact you will be able to use much of this tutorial to set up your home network too. 

~~~ bash
set_network 0 scan_ssid 1 
set_network 0 priority 1  
set_network 0 key_mgmt WPA-EAP  
set_network 0 eap PEAP  
set_network 0 pairwise CCMP  
set_network 0 phase2 "auth=MSCHAPV2"  
~~~
~~~ bash
identity 0 user@educational.email  
password 0 pa$$word4aboveemail  
~~~

This would be the login details you would usually use on your account from your institution.

## Activate connection

~~~ bash
select_network 0
~~~

This enables your connection, hopefully the console will print out a lot of text now and none of it will say "Failed" if it did then try again its possible you've put a letter in the wrong place or if you are certain it doesnt work, send me a message if you fix it and I can add it to this page.

## Save and quit

~~~ bash
save_config
~~~

You could skip this part if you just want to test but I recommend coming back to save after you've done your tests

~~~ bash
quit
~~~

Once this is set up and working in one place it should keep working when you move it too! Well until your institution redacts your account and then it will fail to connect everytime! 

---

# Further Reading:

[WPA Supplicant @ Arch Linux Wiki](https://wiki.archlinux.org/index.php/Wpa_supplicant)  
[WPA_SUPPLICAT + WPA_CLI User Guide](http://www.programgo.com/article/9886626445/)


{{ page.date }} Updated: 2017/03/30 
