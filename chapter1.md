# And so, our story begins...

It was a beautiful fine day on the farm where our story starts. Ruby the cat 
was enjoying the warm sunshine streaming into her window. Her human, Gerry, 
was on the computer. All felt right with the world. 

![panel1](http://www.suzannejmatthews.com/images/aosk/chapter1/panel1.PNG)

Ruby's friend, Pixel, fluttered to the window. "Psst! Ruby!" Pixel called. "You 
should see what Gerry is doing!"

![panel2](http://www.suzannejmatthews.com/images/aosk/chapter1/panel2.PNG)

Ruby glanced at Gerry's screen. Her human was looking at cats on the internet!

"Oh no!" yowled Ruby. She was so confused. Cats? On the Internet? Gerry spent a 
lot of time on the internet, yes, but Ruby never thought that her human would 
be looking at cats. What on earth was Gerry up to? 

"What to do, what to do?" she thought. She had to get to the bottom of this!

![panel3](http://www.suzannejmatthews.com/images/aosk/chapter1/panel3.PNG)

Gerry got up and suddenly walked out the door. Ruby smiled. Gerry didn't know 
her secret. Gerry had no idea that Ruby was no ordinary cat. 

![panel4](http://www.suzannejmatthews.com/images/aosk/chapter1/panel4.PNG)

"Ready to get to the bottom of this mystery, Pixel?" she purred.

"Ready, Scriptkitty!" Pixel chirped.

# Your Goal:

Help Ruby (a.k.a. ScriptKitty) and Pixel figure out what Gerry is doing!

(add some more comics here) 

# Getting to Know the Raspberry Pi

The Raspberry Pi is a _single board computer_ \(or SBC\), where the entirety of the computer is printed on 
a single circuit board. You can think of the RaspberryPi as a _mini_ computer. It has enough resources to 
allow the user to do basic activities such as writing documents, and surfing the internet.  We will use 
the Rapsberry Pi as our main computer for the exercises we will be doing in this book. 

The Raspberry Pi has a lot of the same parts that you may recognize from other computers that you've 
interacted with. One reason the Raspberry Pi is so affordable is that a lot of these components are a lot 
less powerful than those you find desktops and laptops. Let's take a closer look at the Raspberry Pi:

![Pi1](http://www.suzannejmatthews.com/images/aosk/chapter1/PiBoard.jpg)

* **USB port:** these ports are used to connect input devices, such as a mouse or a keyboard.
* **HDMI port:**  used to connect a monitor to the Pi
* **microUSB port:** this is the port where we connect the power cable
* **Ethernet port:** used to connect the Pi to the internet or another computer. 
* **GPIO pins:** useful for interfacing with hardware. We won't use those in these tutorials.
In addition, the Raspberry Pi has integrated wireless and Bluetooth. That means you can connect to the 
internet via a wireless access point, or connect the Pi wirelessly to Bluetooth-enabled devices.

The center black chip is referred to as a _system on a chip_ (or SoC). It houses the Raspberry Pi's 
**Central Processing Unit** (or CPU) along with its **Random Access Memory** (RAM). The CPU allows the 
Pi to perform arithmetic on instructions and data. The RAM stores instructions and data that the CPU 
is actively working on. Together, the CPU and RAM of the SoC represent the Raspberry Pi's "brain".

The data that is stored in the CPU and RAM disappears when you power off your Raspberry Pi. In other 
words, the data stored in the SoC represents _temporary_ storage. The amount of data that can fit 
in the memory of the SoC is also limited. Just like humans write things on paper to remember them later, 
computers write their long-term files and data into _permanent_ storage known as the **hard 
drive**. Unlike the memory on the SoC, the data on the hard drive does not disappear when you power off
your device.

The hard drive of our Raspberry Pi is the tiny microSD card. This microSD card also houses the 
**operating system** (or OS), which is a software layer that sits between the hardware components and 
user applications. Examples of user applications include word processing tools, web browsers, 
and games.  

To get going with the Raspberry Pi, we will start by putting an Operating System on our microSD card.

![Pi2](http://www.suzannejmatthews.com/images/aosk/chapter1/PiBoard2.jpg)

## Preparing the MicroSD card

Before doing anything with the SD card we have to format it. This "preps" our microSD card to receive
the operating system. 

1. Insert the microSD card into the card reader slot using the SD card adapter on your laptop
2. Open File Explorer (or press the windows key + E) and navigate to This PC. 
3. You should see the microSD card under Devices and Drivers
4. Right click on it and choose "Format"
5. Click Start/Ok and close after it is done

Now we can copy the operating system for the RaspberryPi onto the microSD card. The operating system 
for our Raspberry Pi is called Kali Linux. The Linux operating system is a common OS used by 
security professionals and computer scientists. Kali is one of the most popular distributions of 
Linux among security professionals and enthusiasts. Follow the steps below to get Kali on your 
system:

1. From internet: Download and install Win32 Disk Imager (found here https://sourceforge.net/projects/win32diskimager/) 
2. Download the Raspberry image from  XWebsite
3. Open Win32 Disk Imager and navigate to where you downloaded the image and click OK
![setup0](http://www.suzannejmatthews.com/images/aosk/chapter1/setup0.png)
4. Click on the Write button to begin writing the image on the micro SD card.
5. Once it is done, it will appear that the micro SD card is empty. No worries!
6. Eject the card from your laptop and insert it in the RaspberryPi.


The image that we provide you in Step 2 comes pre-installed with all the software you need to get started with 
the Raspberry Pi and explore the concepts along with ScriptKitty.


Your Raspberry Pi is a fully functioning computer. That means when you boot it up, you would see a Desktop
environment, just like when you boot up a laptop! At this point, if you have a separate HDMI enabled monitor, 
a USB keyboard and USB mouse that you can connect your Pi, you can plug those in, power up your Pi, and 
log in. The username is `root` and the password is `toor`. If you can succesfully log in at this point,
congratulations! You are ready to move on to the next chapter. 

The remainder of this chapter allows you to connect to your Raspberry Pi using something called a
_headless configuration_. Instead of connecting separate IO devices to our Raspberry Pi, we are going 
to connect the Raspberry Pi to a laptop. This enables us to interact with our Raspberry Pi using the 
monitor, keyboard and mouse of the laptop! Pretty cool, huh?

To connect to the Raspberry Pi in this manner, we need to install some additional programs on our 
laptop:

## Install supporting software on your laptop (Windows)

To enable us to use our laptop to connec to the Pi, we need a way to remotely connect to it. To do so, 
we will be using something called Secure Shell (SSH). SSH will allow us to connect to the Raspberry Pi 
via a Ethernet cable connected between the Raspberry Pi and your laptop. To use SSH, we will use a 
program called PuTTY. Keep in mind that PuTTY is only necessary if you are using Windows. 

1. Download and install PuTTY (found here https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
![setup1](http://www.suzannejmatthews.com/images/aosk/chapter1/setup1.png)
2. Download and install VNC Viewer (found here https://www.realvnc.com/en/connect/download/vnc/viewer) 
3. Navigate to Network and Sharing Center ( press Windows key and search for Network and Sharing Center)
4. On the right menu go to `Change adapter settings`. Right click on `Ethernet -> Properties`. 
![setup2](http://www.suzannejmatthews.com/images/aosk/chapter1/setup2.png)
6. Click on `Internet Protocol Version 4 -> properties`. On the pop-up window, select `Use the following 
   IP address`. For the IP address type `10.0.0.2` and for the Subnet Mask `255.0.0.0`. Leave everything 
   else blank.
![setup3](http://www.suzannejmatthews.com/images/aosk/chapter1/setup3.png)   
7. Check the box that say `Validate the settings upon exit`. Click `OK` and then click the `X` on the upper 
right hand side of the window to close it. 
8. Keep in mind that if you regularly connect to the Internet using a Ethernet cable, you will not have 
access to internet anymore. When you are done working with the Raspberry Pi, follow steps 4 and 5 and 
select `obtain IP address automatically`. This will bring back the iternet to what it was before.

 
### Connect all your cables
Now that we have installed the additional software on our laptop, we are ready to access the Pi! Let's 
start by connecting our cables. You will need: a microUSB to USB cable (same cable used to charge a phone),
and a crossover (or Patch) ethernet cable.


1. Make sure your laptop is on and that the Pi starts out turned off.
2. Connect the Ethernet cable from the Pi to your laptop's Ethernet port.
3. Plug in the microUSB power cable into your Pi. Connect the USB end into your laptop. This will supply 
power to your Raspberry Pi.

## Access your Raspberry Pi!
Now it's time for the moment of truth! We get to boot up our machine! Do the following:
1. Open `PuTTY.exe`. You should find this in Local Disk `C -> Program Files -> Putty`
![setup4](http://www.suzannejmatthews.com/images/aosk/chapter1/setup4.png)
2. In the Host Name box, write `10.0.0.3` and in the `Saved Sessions` write `RaspberryPi`. Press `Save` and 
then `Open`. 
![setup5](http://www.suzannejmatthews.com/images/aosk/chapter1/setup5.png)
3. A black window should pop up and ask for a user name and password. (Username: root  Password: toor). If a 
   security alert shows up, select Yes.
4. If this works, pat yourself on the back. You are now connected to the RaspberryPi via the Command Line! 
Hooray! While you can do all of our exercises in this interface, let's get a Desktop interface for now.
![vnc1](http://www.suzannejmatthews.com/images/aosk/chapter1/vnc1.png)
5. In this window, type `bash startvnc.sh` and press `Enter`. Go ahead and minimize the window if you wish. 
**DO NOT CLOSE IT**
![vnc2](http://www.suzannejmatthews.com/images/aosk/chapter1/vnc2.png)
6. Press the windows key and search for VNC viewer and open it. Once it opens, go to `File -> New Connection`.
7. In the VNC server box write `10.0.0.3:5900` and in the Name box write a name for your RaspberryPi. 
Press `OK`. 
![vnc3](http://www.suzannejmatthews.com/images/aosk/chapter1/vnc3.png)
8. You should see an icon with the chosen name. Double click on it.
![desktop](http://www.suzannejmatthews.com/images/aosk/chapter1/desktop.png)
9. Next, you will be asked for a username and password. Use the same ones from step 3.

If everything worked as planned, you should now see a Desktop pop up, just like a normal computer. Great 
job! If you have a wireless connection nearby you can connect it to internet and start navigating.

**Going forward:** Every time you want to access your RasperryPi, you have to open PuTTY, click on 
Raspberry, Load and Open. Repeat steps 3-5. Open VNC viewer and follow step 9.

## Troubleshooting

**Q: How can I tell if my monitor is HDMI enabled?**
A: Look at the back of the monitor. You should see a port similar to the HDMI port on the Raspberry Pi.
If you don't have that port, the monitor is not HDMI enabled. Remember that you need a HDMI cable to 
connect the Pi to your monitor!

**Q: I don't have a HDMI computer monitor. What are my other options?**
A: If you don't have a HDMI computer monitor, don't worry! A lot of modern TVs have HDMI ports. You 
can use your TV as a monitor by connecting the Pi directly to your TV using a HDMI cable!

If you don't have a HDMI-enabled monitor at home, see if you can get a patch cable and microUSB cable. 
You can also ask your teacher if you can use the school's computer monitors to connect to your Raspberry Pi.

**Q: I don't have a windows laptop. I have a macbook.  Can I still use the Raspberry Pi?**
A: Absolutely! You don't need to install Putty, but go ahead and install OpenVNC. To connect to your 
laptop using using your macbook, open up the `Terminal` application, and type in the command:
`ssh root@10.0.0.3`. Make sure that you connect your Ethernet cable to your Pi and laptop and power it up 
first though!

**Q: My laptop doesn't have an Ethernet port! What do I do?**
A: A lot of modern laptops are getting rid of the Ethernet port. Not to worry though -- you can connect to 
the Rapsberry Pi using a USB to Ethernet dongle. Some dongles require that you install a driver to get it 
to work. Make sure that you install any needed drivers. If you run into issues, ask your teacher or a parent 
for help.

**Q: When I try to connect using PuTTY, I get an error that says "Refused Connection" what do I do?**
A: Open up a command window and type `ipconfig`. If your IP address does not show up as `10.0.0.2`, that 
means that your network configuration isn't right. Ensure that your Ethernet cable is connected to your 
computer and the lights on the Ethernet port is flashing. If this doesn't work, try unplugging the 
power cable to your Pi, and reconnecting it. This is called "power-cycling". Usually, power cycling is 
sufficient.

**Q: I don't see any Ethernet lights when I try to connect to my Pi!**
A: Is your Pi powered on? If so, what color is the light? If the light is red, that means that there 
might be something wrong with your microSD card. Try reimaging the card by redoing the steps in the 
"Preparing the MicroSD card" section. 

If the LED is green, but you still aren't seeing any lights on the Ethernet port, check the Ethernet 
cable. You may need a crossover or patch cable. This is different from the standard Ethernet cable, 
since crossover cables are used to connect to computers together.



