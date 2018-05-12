---
layout: post
title: "ps3 sixaxis controller + ubuntu = fun"
comments: false
categories:
  - hardware
  - ubuntu
  - games
---

The Problem
-----------


![Overboard]({{ "/images/game-room.jpg" | absolute_url }})

I like this room.  But well, It's just not for me.  Instead I like playing old
games with emulators, like <a href="http://www.zsnes.com/">zsnes</a> (Super
Nintendo) or <a href="http://mamedev.org">MAME</a> (Arcade) or even <a
href="http://www.dolphin-emulator.com/">dolphin</a> (Gamecube).  And when
playing emulated games, I recommend Ubuntu, even if other operating systems
have a marketshare edge (for now).

Ubuntu has been a first class citizen with many emulators
for some time now.  I think the idea of a free operating system running
mutliple console platforms on commodity hardware just has a certain
nerd-charm, so the platform has recieved a lot of attention from emulator
writers.  But to get a true console/arcade experience you need to move beyond the
keyboard ... to a gamepad of some kind.

Admit it: arcade and console games are more fun to play with a gamepad.
Usually the system-specifc controller is the best, but a good one like the
sixaxis controller, or the xbox controller are reasonable substitutes for the
platform native varieties.  You can get close to that picture without being the
guy in that picture.

10 years ago, Linux distributions were downright awful at using gamepads.
Given <a href="http://www.motioninjoy.com/download">how hard and adware ridden</a>
this process can be in other operating systems, I really wasn't looking
forward to configuring my gamepad on Ubuntu today.

The Solution
------------

My, how the landscape has changed with Ubuntu.  To set up a <a
href="https://en.wikipedia.org/wiki/Sixaxis">Sixaxis</a> controller under
Ubuntu, follow the steps below:

 1. Plugin your sixaxis controller over USB and press the `PS` button.

Yes folks, that is it.  I put in a single list item to illustrate how poor my
writing skills are and how easy this process is.

Reality Check
-------------

Now that your head is spinning from awe of how easy things have become in
Ubuntu, it's time to temper that elation with some facts.  Things don't always
go right.  Your needs maybe different than mine, and your controller may not
work right away in exactly the way you want it to.  So, I thought a small
section on tips and configuration might be in order.

Let's test that controller:

``` bash
sudo apt-get install joystick
sudo tail -f /var/log/syslog    # In one window
jstest /dev/input/js0           # In another window (once you plug in)
```

If things are going right, when you plugin the controller you will see output like this in your syslog:

```
Sep 25 20:45:43 starbuck kernel: [  205.732300] usb 2-1.2: new full-speed USB device number 4 using ehci-pci
Sep 25 20:45:43 starbuck kernel: [  205.866723] usb 2-1.2: New USB device found, idVendor=054c, idProduct=0268
Sep 25 20:45:43 starbuck kernel: [  205.866738] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 25 20:45:43 starbuck kernel: [  205.866747] usb 2-1.2: Product: PLAYSTATION(R)3 Controller
Sep 25 20:45:43 starbuck kernel: [  205.866755] usb 2-1.2: Manufacturer: Sony
Sep 25 20:45:43 starbuck mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2"
Sep 25 20:45:43 starbuck mtp-probe: bus: 2, device: 4 was not an MTP device
Sep 25 20:45:43 starbuck kernel: [  206.045910] sony 0003:054C:0268.0005: Fixing up Sony Sixaxis report descriptor
Sep 25 20:45:43 starbuck kernel: [  206.089500] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0/input/input14
Sep 25 20:45:43 starbuck kernel: [  206.093696] sony 0003:054C:0268.0005: input,hiddev0,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.7-1.2/input0
S
```

Now, run the `jstest /dev/input/js0` command.  When you press the buttons, you
should see numbers changing on your screen.  When I first did this, I did not.
It turns out I had to <a
href="https://support.us.playstation.com/app/answers/detail/a_id/444/~/troubleshoot-dualshock-3%2Fsixaxis-controllers">reset
the controller to factory defaults</a>, and everything worked fine after that
(paperclip-sized-hole underneath the controller close to the left trigger
buttons).

Do you want some lower-level configuration?  If you are running a sixaxis
controller on Ubutnu, you just might be that type of person.  Go checkout the
<a href="https://help.ubuntu.com/community/Sixaxis">Ubuntu Sixaxis page</a>,
which talks about how to pair the device over bluetooth, even how to use the
really cool QTSixA tool.

But enough of reality, if you have /dev/input/js0 and jstest works, you are
golden.  All your games and emulators should now "just work".

Thanks Ubuntu developers and community, and happy gaming!
