# And so, our story begins...

Introduce scriptkitty, the main story line, first setup tutorial.

===

# About the Raspberry Pi

The Raspberry Pi is a _single board computer_ \(or SBC\), where the entirety of the computer is printed on a single circuit board. We will use the Rapsberry Pi as our main computer for the exercises we will be doing in this book. Let's take a closer look at the Raspberry Pi:

You can think of the RaspberryPi as a _mini_ computer. It has enough resources to allow the user to do 
basic activities such as writing documents, and surfing the internet.  

The Raspberry Pi has a lot of the same parts that you may recognize from other computers that you've 
interacted with. One reason the Raspberry Pi is so affordable is that a lot of these components are a lot 
less powerful than those you find desktops and laptops:

![Pi1](http://www.suzannejmatthews.com/images/aosk/chapter1/PiBoard.jpg)

* **USB ports:** these ports are used to connect input devices, such as a mouse or a keyboard.
* **HDMI port:**  used to connect a monitor to the Pi
* **microUSB port:** this is the port where we connect the power cable
* **Ethernet port:** used to connect the Pi to a laptop/desktop. 
* **GPIO pins:** useful for interfacing with hardware. We won't use those in these tutorials.

The center black chip is referred to as a _system on a chip_ (or SoC). It houses the Raspberry Pi's 
**Central Processing Unit** (or CPU) along with its **Random Access Memory** (RAM). The SoC represents the 
Raspberry Pi's "brain". The RAM acts as the "memory", storing information that the Raspberry Pi working on, 
with the CPU performing calculations on that information. 

Not all data can fit in the memory of the SoC. Just like you need to write things down on paper to remember 
them sometimes, computers write their long-term files and data into permanent storage known as the **hard 
drive**. The hard drive of our Raspberry Pi is the tiny microSD card. This microSD card also houses the 
**operating system**, which is a software layer that ensures that the hardware plays nice with all of the 
programs we write for it. This will be the first thing we will set up.

![Pi2](https://www.suzannejmatthews.com/images/aosk/chapter1/PiBoard2.jpg)

## Preparing the MicroSD card

Before doing anything with the SD card we have to format it. This "preps" our microSD card. 

1. Insert the microSD card into the card reader slot using the SD card adapter
2. Open File Explorer (or press the windows key + E) and navigate to This PC. 
3. You should see the microSD card under Devices and Drivers
4. Right click on it and choose "Format"
5. Click Start/Ok and close after it is done

Now we can copy the operating system for the RaspberryPi onto the microSD card:
1. From internet: Download and install Win32 Disk Imager ( found here https://sourceforge.net/projects/win32diskimager/) 
2. Download the Raspberry image from  XWebsite
3. Open Win32 Disk Imager and navigate to where you downloaded the image and click OK
4. Click on the Write button to begin writing the image on the micro SD card.
5. Once it is done, it will appear that the micro SD card is empty. No worries!
6. Eject the card from your laptop and insert it in the RaspberryPi.

The image that we provide you comes pre-installed with all the software you need to get started with the Pi.
In the next step, we are going to connect up all our cables and connect to our Pi!

## Install supporting software on your laptop

Your Raspberry Pi is a fully functioning computer. That means when you boot it up, you would see a 
Desktop environment, just like when you boot up a laptop! Let's get this part set up next.

1. Download and install PuTTY (found here https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) 
2. Download and install VNC Viewer (found here https://www.realvnc.com/en/connect/download/vnc/viewer) 
3. Navigate to Network and Sharing Center ( press Windows key and search for Network and Sharing Center)
4. On the right menu go to `Change adapter settings`. Right click on `Ethernet -> Properties`. 
6. Click on `Internet Protocol Version 4 -> properties`. On the pop-up window, select `Use the following 
   IP address`. For the IP address type `10.0.0.2` and for the Subnet Mask `255.0.0.0`. Leave everything 
   else blank.
7. Check the box that say `Validate the settings upon exit`. Click `OK` and then click the `X` on the upper 
right hand side of the window to close it. 
8. Keep in mind that if you regularly connect to the Internet using a Ethernet cable, you will not have 
access to internet anymore. When you are done working with the Raspberry Pi, follow steps 4 and 5 and 
select `obtain IP address automatically`. This will bring back the iternet to what it was before.


## Connect all your cables

1. Make sure your laptop is on and that the Pi starts out turned off.
2. Connect the Ethernet cable from the Pi to your laptop's Ethernet port.
3. Plug in the microUSB power cable into your Pi. Connect the USB end into your laptop. This will supply 
power to your Raspberry Pi.

## Access your Raspberry Pi!

Now it's time for the moment of truth! We get to boot up our machine! Do the following:
1. Open `PuTTY.exe`. You should find this in Local Disk `C -> Program Files -> Putty`
2. In the Host Name box, write `10.0.0.3` and in the `Saved Sessions` write `RaspberryPi`. Press `Save` and 
then `Open`. 
3. A black window should pop up and ask for a user name and password. (Username: root  Password: toor). If a 
   security alert shows up, select Yes.
4. If this works, pat yourself on the back. You are now connected to the RaspberryPi via the Command Line! 
Hooray! While you can do all of our exercises in this interface, let's get a Desktop interface for now.
5. In this window, type `bash startvnc.sh` and press `Enter`. Go ahead and minimize the window if you wish. 
**DO NOT CLOSE IT**
6. Press the windows key and search for VNC viewer and open it. Once it opens, go to `File -> New Connection`.
7. In the VNC server box write `10.0.0.3:5900` and in the Name box write a name for your RaspberryPi. 
Press `OK`. 
8. You should see an icon with the chosen name. Double click on it.
9. Next, you will be asked for a username and password. Use the same ones from step 3.

If everything worked as planned, you should now see a Desktop pop up, just like a normal computer. Great 
job! If you have a wireless connection nearby you can connect it to internet and start navigating.

**Going forward:** Every time you want to access your RasperryPi, you have to open PuTTY, click on 
Raspberry, Load and Open. Repeat steps 3-5. Open VNC viewer and follow step 9.

## Troubleshooting

1. If throughout the tutorial, you encounter any error message, press CANCEL.
2. A common problem might be when trying to connect to the Pi using Putty. If you receive an 
error about a refused connection, go back to step 4 and do the tutorial again. If it continues to be a 
problem, try to change the Ethernet cable.



