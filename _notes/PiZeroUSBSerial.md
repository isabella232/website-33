---
layout: post
permalink: /Pi-USB-Serial/
title: How to setup a Pi Zero in Serial Gadget Mode in a secure system
date: 2017/04/18
colour: orangered
link-color: white
published: true
---

# {{ page.title }} 

---
{: .thick-rules}


## Contents:

|---
| [Ingredients](#ingredients)			|
| [TL;DR](#tldr)	        			|
| [Why?](#why)                          |
| [How?](#how)                          |
| [Further Reading](#further-reading)	|
|===
{: .contents-section}

---

## Ingredients:

1 x Pi Zero (or A+ or Zero W)  
1 x Micro SD card of sufficant size  
1 x Micro USB Cable   
1 x Computer that can read and edit files, mount ext4 and you can install or use a serial terminal with (i.e putty or screen)   

---

## TL;DR:

Mount a flashed MicroSD's boot partition
~~~ bash 
echo "dtoverlay=dwc2" >> config.txt
sed -i -e "s/rootwait/rootwait modules-load=dwc2,g_cdc" /media/amnesia/boot/cmdline.txt
~~~
cd to the root of the other partition.
~~~ bash
ln -s lib/systemd/system/getty@.service etc/systemd/system/getty.target.wants/getty@ttyGS0.service
~~~
Make sure the changes are wrote 
Plug in Pi Zero via data usb
Access via a serial terminal (i.e. screen or putty)

---

## Why?:

When I use Tails OS (which is my primary OS) and I'm setting up a Pi Zero W (as I do very regularly) I have an issue of either using a USB TTY or setting it up else where and just sshing into it.  
I knew that the Pi Zero supported gadget mode for Ethernet out of the box (with some small changes to the config files) but because of the way networking works on Tails it is very difficult (and possibly impossible) to connect to the ethernet gadget and resolve the "raspberrypi.local" address.  
I knew that the Pi Zero could be used as a serial gadget as well but all of the tutorials required you to have access to the terminal already, which in my case (barring a USB TTY) is impossible. 
I'm sure that this will be usful in some other cases aswell. 

---

## How?:

I'm using Tails OS 3.0 beta 3 right now so I'll be going through step by step on this from blank SD to working gadget. You will need to have an administrator password set otherwise you'll have to do some weird stuff (which may be useful to know just for kicks or if you need to do something real quick)

1. Download Raspbian, you can use the website or download using wget, in Tails you will need to put "torsocks" in front of the wget as you need to run it through the Tor proxy. 

### For lite use:
~~~ bash
wget http://downloads.raspberrypi.org/raspbian_lite_latest -O raspbian.zip
~~~

### For regular use:
~~~ bash
wget http://downloads.raspberrypi.org/raspbian_latest -O raspbian.zip
~~~

2\. Unzip the file to get a image, you can also just doubleclick on the zip file if you prefer that  

~~~ bash
unzip rasbian.zip
~~~

3\. Insert the Micro SD card
I like to run a "ls /dev/sd\*" before plugging my card in so that I know what devices are currently plugged in, after plugging in the card I run it again and note the additional device. (i.e if /dev/sdb was only there after plugging in the card then I use that) 

4\. Flash Raspbian
I prefer using dd, but if you prefer GUI applications you can use the "Disks" application in Tails. Just click on your SD card in the left hand column, then click the 3 line button (burger button) in the top right hand corner of the window, select "Restore Disk Image" and then go find the ".img" file, likely in "Tor Browser" if you downloaded raspbian from the website.

using dd would be, being careful to flash the correct device:
~~~ bash
dd if=*raspbian*.img of=/dev/sdb bs=4096 status=progress
~~~

5\. Mount boot
Open up "Files" and click on "boot" on the left hand column.

6\. Make inital config changes
Add "dtoverlay=dwc2" to the bottom of config.txt on its own line
Add "modules-load=dwc2,g_cdc" after "rootwait" in cmdline.txt, making sure there are spaces either side.

In the terminal this would be
~~~ bash 
echo "dtoverlay=dwc2" >> config.txt
sed -i -e "s/rootwait/rootwait modules-load=dwc2,g_cdc" /media/amnesia/boot/cmdline.txt
~~~

Make sure everything is saved correctly.

7\. Unmount the boot partition

Click the little eject button next to boot in "Files".

8\. Mount the other partition that appears next to boot in "Files"

9\. Enable the System D service
Now this is where the magic happens. Open a terminal if you havent already,
change directory to the micro SD cards partition (usually mounted at /media/amnesia/ followed by a long string of numbers and letters, you can usually just autocomplete this by hitting tab a couple of times, if you have multiple drives mounted then you can start typing whatever the long string of characters is and then hit tab to autocomplete it). When you use ls it should show you various folders like bin, boot, dev, home, lib, media, etc, etc. 

To enable the serial service you'd usually run a command, systemd enables services by linking a file to a name (kinda like a shortcut) you don't really need to know about it but we can use it to our advantage and just link it ourself. 

You may need to run this as sudo. (read: most likely you will put "sudo " before ln)

~~~ bash
ln -s lib/systemd/system/getty@.service etc/systemd/system/getty.target.wants/getty@ttyGS0.service
~~~

10\. Unmount and Plug everything in to the Pi, this time making sure to connect to the computer with a Micro SD

11\. Look for the /dev/ttyACM0 port appearing when you run "ls /dev/tty\*"

12\. Install a serial terminal compatible program 

In tails I recommend screen
~~~ bash
sudo apt update 
sudo apt install screen -y
~~~

13\. Open the serial device with screen (or whatever program you are using)

You may need to run this as root.
~~~ bash 
screen /dev/ttyACM0
~~~

14\. And thats it!

### Bonus!:

If you've accidentally started tails without an admin password you can't set it up, but if you need to use it and don't need to do much work you can open /dev/ttyACM0 with cat, and echo commands into it!

---

## Further Reading:

TODO

{{ page.date }} Updated: 2017/04/27
