---
layout: post
title:  "Tips for setting up a Minecraft server using a Raspberry Pi"
author: simon
categories: [ Raspberry Pi ]
tags: [red, yellow]
image: simondotm/images/picraft.jpg
description: "Tips for setting up a Minecraft server using a Raspberry Pi."
featured: true
hidden: true
toc: true
---

Running your own Minecraft server seems like a pretty good idea if, like me, you have one or more kids (plus their friends) who want to team up and build a world together. Yes, they can host a server on their computers, but that only works when they have their computers on and running Minecraft, so a dedicated server is the best solution all round.

There’s loads of public servers out there but my lot tend to grumble endlessly about the inconsistent characters they encounter  in internet land who don’t seem to want to play the same way as them, so having their own private world makes sense, and a Pi saves you the monthly cost of renting a private realm.

There’s already tons of tutorials out there for getting a Minecraft server up and running on your Raspberry Pi, so I’m not going to repeat the nitty gritty. Instead, I’ve put together a handy heads up attack plan with some useful links so it might save you a bit of time hunting around once you start out on this quest.

## What you’ll need:

1. A [Raspberry Pi](https://www.amazon.co.uk/Raspberry-Pi-Model-Quad-Motherboard/dp/B01CCOXV34/ref=sr_1_2?s=computers&ie=UTF8&qid=1463347196&sr=1-2&keywords=raspberry+pi+3) – I really recommend a Pi 2 or better. Anything less and the server will struggle to work nor satisfy lag-hating youtube generation kids.
2. A [decent fast micro SD card](https://www.amazon.co.uk/SanDisk-Android-microSDHC-Frustration-Packaging/dp/B013UDL5V6/ref=sr_1_2?s=computers&ie=UTF8&qid=1463347268&sr=1-2&keywords=16gb+micro+sd+card) – 4Gb is fine. 8Gb is plenty. 16Gb cards tend to be a little faster, and definitely more than enough sizewise.
3. A [standard HDMI cable](https://www.amazon.co.uk/Pi-Hut-HDMI-Cable-Raspberry/dp/B00GHNLN0U/ref=sr_1_1?ie=UTF8&qid=1463347304&sr=8-1&keywords=hdmi+cable+raspberry+pi) & TV/monitor
4. A [micro USB cable](https://www.amazon.co.uk/Hapurs-Raspberry-Micro-Cable-Switch/dp/B0124Q8E3M/ref=sr_1_15?ie=UTF8&qid=1463347356&sr=8-15&keywords=micro+usb+raspberry+pi) and some sort of USB power source (phone charger etc.)
5. A standard USB keyboard. I’m sure you have one knocking around somewhere.
6. A standard Cat5/Cat5e/Cat6 RJ45 [network cable](https://www.amazon.co.uk/Belkin-Cat5e-Snagless-Patch-Cable/dp/B00009VGS3/ref=sr_1_12?ie=UTF8&qid=1463347631&sr=8-12&keywords=network+cable)
7. You’ll need to connect your Pi to a TV just once initially so that you can configure SSH (secure shell access – it’s cool, it’s like hollywood style hacking into a remote server) but after that, all the gory details can be done remotely over the network using any old PC.

## Your mission objectives:

1. Download an OS image ([Raspbian Lite](https://www.raspberrypi.org/downloads/raspbian/) or [MinecraftPi](https://www.raspberrypi.org/forums/viewtopic.php?t=75882_*) and write the image to an SD card
2. Connect your Pi to a keyboard and the display and [enable SSH via raspi-config](https://pimylifeup.com/raspberry-pi-ssh/)
3. Unplug everything and move your Pi to where it’s going to be permanently connected to the network. Connect the Pi to your main home internet router using the network cable, and power it up. (I plugged mine straight into my BT Homehub router, and powered it off the USB slot on the back of the router). .
4. Now you can [remotely log into the Pi](https://www.raspberrypi.org/documentation/remote-access/ssh/windows.md) using [Putty.exe](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) on Windows (or ssh on Linux) and complete all of PiMyLifeUp’s excellent [MC server setup](https://pimylifeup.com/raspberry-pi-minecraft-server/) tutorial – don’t forget to follow the last bit of this tutorial; setting up the Pi so that it automatically runs the server when powered up.
5. That’s it – you’re done! Bask in the glow of being a tech-wizard to your kids. Now the MC server is running you can leave it powered on and running on your home network for everyone to use whenever they like.

### For bonus points:

* I recommend [renaming the hostname](http://www.howtogeek.com/167195/how-to-change-your-raspberry-pi-or-other-linux-devices-hostname/) of the Pi to something more personal and memorable eg. “myminecraftserver” so it’s easy to find in Minecraft
* I also recommend adjusting your router’s DHCP settings so that your Pi always gets given the same IP address on your network
* Finally, if you want to enable folks outside your home network to connect to your server, you’ll probably need to setup a dynamic DNS. I’ve posted a follow up article to cover this.

Enjoy!

### Notes

* The tutorial I linked to uses the [Spigot server package](https://www.spigotmc.org/). It works well, and is well supported. It allows you to run vanilla Minecraft or install mods/plugins as you like.
* *I haven’t tried MinecraftPi, but do let me know if you it works for you!
* Remember that performance of your server depends a great deal on the specs of your Raspberry Pi:
* Model A’s are pretty much unsuitable for Minecraft
* Model B’s came in two flavours – early versions were 256Mb and later versions were 512Mb. If you have the 256Mb version, it will struggle to run reliably.
* So if you are going to buy a Pi just for this purpose, it’s definitely worth getting a Pi2 or a Pi3. There’s 1Gb of RAM and a nice quad core CPU on these, which handles Minecraft with ease.
* One more tip I have is to make sure you get a fast SD card – class 10 or above with 80Mb/sec data transfer rating. They are amazingly cheap these days!


# Part 2 - Opening Access To Your Server
So now you’ve setup your shiny new Minecraft server on your Raspberry Pi, and everyone in your house can connect and build a beautiful world together. But now you’re thinking – wouldn’t it be great if our friends, sorry I mean our kids’ friends, could also connect to it?

Well, it’s easier than you think. Again, there’s plenty of detailed tutorials out there, but I like simple guides so here’s one to help you on your Bonus mission.

## What you’ll need:

Your Raspberry Pi, running a dedicated Minecraft server and connected to your home router
Ideally, a home internet router that has a facility for Port Forwarding and DynamicDNS (I’m using a BT Home Hub, so I’ll use that as an example)

## Your next mission objectives:

1. Go to the [GRC shield’s up website](https://www.grc.com/x/portprobe=25565), you will probably (hopefully?) see port showing 25565 showing as “Stealth mode” – this means your home router is doing its job well and denying all of the spooky internet hackers out there any access to your home network
2. Connect to your router’s web admin page in a web browser
3. Setup a port forward for ANY protocol on port 25565 to your Raspberry Pi device (identified either by it’s hostname, or by it’s IP address on your home network)
4. Go to the [GRC shield’s up website](https://www.grc.com/x/portprobe=25565) again, this time you should see the port is now showing as “Open”
5. Voila! We’ve opened up outside access for port 25565 and routed all traffic to our Pi Minecraft server!
6. The GRC site also shows you your current IP address, so for testing purposes you can try connecting to your Minecraft server by entering this IP address into the Minecraft “Join Server” page and it should connect just fine.

## Port forwarding instructions for BT Home Hub 5:

1. Log into your BT Home Hub web admin dashboard (usually http://192.168.1.254/)
2. Go to “Advanced settings” -> “Port forwarding”
3. Click “Manage games and applications” -> “Add new game or application”
4. Enter “Minecraft”, No to “copy existing game”, set “Protocol” to Any, Port range 25565-25565, Translate To 25565-25565, click “Add”, then “Apply”
5. Navigate back to the “Port forwarding” page, select “Minecraft” from the “Game or Application” drop down, and then select your Raspberry Pi device from the “Device” drop down, Click “Add”, then “Apply”

## Your final mission:
IP addresses suck – I want something easy to remember!

The above is all fine and dandy, but sadly, home internet providers tend to use dynamic IP addresses. This means that your IP changes fairly frequently, so if you went and told all your friends about your shiny new Minecraft server and gave them your IP address to connect to, a) they or you would probably forget the number, or b) it’d work for a while, but soon would stop, because your IP address will change in few days or weeks.

This is where [Dynamic DNS](http://www.noip.com/support/knowledgebase/getting-started-with-no-ip-com/) comes in. The idea is that your router will continually tell some other server what its current IP address is. That server then stores that new IP against some domain name you’ve created. This way you only need to remember your domain name, and no-one needs to care if your IP address changes – the magical internet figures it all out for us.

So here’s how to dodge all that IP nonsense:

1. Create a free account with [NoIP](http://www.noip.com/) and create a fancy new free domain name for your minecraft server eg. “jeeperscreepers.ddns.net”
2. Configure the DynamicDNS settings on your home router with your NoIP credentials and your new domain name (seel below)
3. Boom! Done. Now, tell your friends to join your awesome new server called “jeeperscreepers.ddns.net” and it all just works!

Be careful who you tell though as it’ll only be a private server if you keep it private! So don’t go posting the domain name for your server on Twitter without expecting a bunch of unruly internet strangers to login and mess with ur world.

### Dynamic DNS instructions for BT Home Hub 5:

1. Log into your BT Home Hub web admin dashboard again
2. Go to “Advanced Settings” -> “Broadband” -> “Dynamic DNS”
3. “Dynamic DNS server enable”, click Yes
4. “Service” -> select “NoIP”
5. “Use multiple hosts” -> No
6. Enter your NoIP server domain you setup earlier eg. “jeeperscreepers.ddns.net”
7. Enter your NoIP account login details – username & password
8. Click “Apply”, then click “Refresh”
9. Done! If all went well you’ll see “Dynamic DNS service status: Connected – IP address is current, no update performed”
10. Away you go.

Hope that helps!
