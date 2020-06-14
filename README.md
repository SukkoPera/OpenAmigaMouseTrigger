# OpenAmigaMouseTrigger
OpenAmigaMouseTrigger is an Open Hardware PCB that allows using the state of the mouse buttons at power-up of an Amiga computer to trigger features of other boards, instead of using physical switches. This is mainly useful for controlling a [Kickstart Switcher](https://github.com/SukkoPera/OpenKickstartSwitcher) or a [Drive Switcher](https://github.com/SukkoPera/OpenAmigaDriveSwitcher).

![Board](https://raw.githubusercontent.com/SukkoPera/OpenAmigaMouseTrigger/master/doc/render-top.png)

### Summary
If you install a Kickstart Switcher in your Amiga, you might not want to drill a hole in its venerable case in order to install a switch to select the Kickstart of your choice. Back in the day, it was common to do your selection by holding or not the left mouse button at power-up. OpenAmigaMouseTrigger is a reimplementation of this mechanism on a small isolated board, so that you can use it to trigger anything you want, and not be limited to Kickstarts or even to Amiga computers.

OpenAmigaMouseTrigger also features a second channel, so you can generate up to four different signal combinations.

### Assembly
Solder all components to the board. No particular order is recommended, but starting with the smaller components might be a good idea.

### Installation
Connect the signals you want to sample at power-up to I1 and I2. Connect the signals you want to drive to O1 and O2. Install R1 and R2 if the input signal needs pull-up resistors.

OpenAmigaMouseTrigger was designed to work with [OpenKickstartSwitcher](https://github.com/SukkoPera/OpenKickstartSwitcher). You can also use it in other scenarios, but the default component values were tuned for this case. While it would be great to use both mouse buttons as input signals, [the right mouse button is not usable for this](https://www.dropbox.com/s/n4spcituqtnby74/MouseSwitcherFailSmall.png), probably because of how the Amiga sampling circuit was designed. I suggest to use the port 2 joystick fire button as the second selection signal. This is ideal if you put DiagROM + Kickstart 1.3 + Kickstart 3.1 on your OpenKickstartSwitcher, since you won't use DiagROM too often, and you'll be able to select the other two ROMs with the left mouse button.
If your mouse buttons already are used for boot menus or similar, you can use port 2 joystick directions instead. No movement of the joystick will launch your default ROM, you'll be able to select the other two ROMs by holding your joystick in the direction of your choice. Note that to be able to choose between four ROMs, the fourth direction will have to be diagonal, so you have to pick two adjacent directions . Signal 1 is Up, signal 2 is Down, signal 3 is Left, and signal 4 is Right, see image for reference ![Signal 1 is Up, and signal 4 is Right](https://raw.githubusercontent.com/SukkoPera/OpenAmigaMouseTrigger/master/doc/joystick_directions.jpeg)

R4 is a bleeder resistor used to discharge C1 quickly when power is removed, be sure to allow at least 4-5 seconds before turning your system back on.

If you use OpenAmigaMouseTrigger in a different scenario, you might want to alter the sampling delay at power-up. This can be done by changing the values of C1 and R3, which form a simple RC network which drives the flip-flip clock signal. The default values will yield a delay or around 50 us, which is quite good for the Amiga (it has a power-on reset pulse after about 100 us) but note that actual capacitor values may differ a lot from the nominal capacity, even 20%, so you might need to do some tweaking. You might also want to experiment with different values of R4, if your C1 has a largely different capacity.

### License
OpenAmigaMouseTrigger is Open Hardware. If you make any modifications to the board, please contribute them back.

### Support the Project
Since the project is open you are free to get the PCBs made by your preferred manufacturer, however in case you want to support the development, you can order them from PCBWay through this link:

[![PCB from PCBWay](https://www.pcbway.com/project/img/images/frompcbway.png)](https://www.pcbway.com/project/shareproject/OpenAmigaMouseTrigger_V2.html)

You get cheap, professionally-made and good quality PCBs, I get some credit that will help with this and [other projects](https://www.pcbway.com/project/member/shareproject/?bmbid=41100). You won't even have to worry about the various PCB options, it's all pre-configured for you!

Also, if you still have to register to that site, [you can use this link](https://www.pcbway.com/setinvite.aspx?inviteid=41100) to get some bonus initial credit (and yield me some more).

Again, if you want to use another manufacturer, feel free to, don't feel obligated :).

### Get Support
If you need help or have questions, you can join [the official Telegram group](https://t.me/joinchat/HUHdWBC9J9JnYIrvTYfZmg).
