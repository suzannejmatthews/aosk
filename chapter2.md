# The Ghost in the Wire

![panel1](http://www.suzannejmatthews.com/images/aosk/chapter2/panel1.jpg)

Gerry swung the door open wide, and marched in like on a mission, immediately 
sitting down at the desk and turning on the computer. 
"I wonder what Gerry's up to?" Ruby pondered. "What if Gerry's looking at cats again!?!"
Ruby walked over to Gerry's computer to take a look, but she couldn't quite 
see what was going on. Her curiosity got the best of her.


![panel2](http://www.suzannejmatthews.com/images/aosk/chapter2/panel2.jpg)

As Ruby squirred to her room, by pleasant surprise, Pixel fluttered in through the window.

![panel3](http://www.suzannejmatthews.com/images/aosk/chapter2/panel3.jpg)


![panel4](http://www.suzannejmatthews.com/images/aosk/chapter2/panel4.jpg)

The purpose of this tutorial is to show the students how vulnerable they 
can be on an unsecured network (Like Gerry's home network) by demonstrating how 
a packet sniffer like WireShark can be used to monitor network activity.

<!-- The purpose of this tutorial is to show the students how vulnerable they can be 
on an unsecured network. While it is fun and interesting to read emails, find 
passwords and see what anyone else is searching, it is important to mention 
that this tutorial is performed in a secure environment and the network 
packets are specifically created for this activity. The legality of capturing 
and inspecting packets is a gray area and thus, you should not attempt to do 
anything learn in this tutorial outside of the Raspberry Pi. -->


## Networks Fundamentals
Let's start by talking about networks. A **network** is simply a collection of 
computers or other devices that are connected together some way, usually via a 
router. 

A **router** is a simple device that is capable of transferring information 
between the devices that are connected to it. These devices could be different 
computers, printers, or even other routers who can then pass the information 
on.

Each computer on the network is assigned an **IP address**. This address is 
subject to change. If the user connects to the internet via a different router 
or at a different time, they may have a different IP address. Contrast this to 
the **MAC address**, which is unique to a particular device. If you bring a 
router down, you affect all the devices that are connected to it, and any 
other routers it is connected to. If a router is offline, the devices connected to 
it are also offline, as they cannot obtain IP addresses. Thus, the internet at 
any particular time can be defined as the set of visible routers.

## How is information sent on the internet?

Let's talk about packets. If you want to send something over the internet 
(say sending a picture to your grandma), it gets broken down into tiny pieces 
called packets.

![panel3](http://www.suzannejmatthews.com/images/aosk/chapter2/packet.PNG)

Packets are a lot like the packages you send in the mail:
* The **packet header** contains the information on how the packet should be 
  handled, similar to the labels you see on a a regular package. 
	* The **source and destination IP address** is like the return and 
	  address labels you place on packages you mail. 
	* The **port and protocol** indicate how the packet should be routed, 
	  similar to the priority mail stickers you see. The header is designed 
	  to assist the router to get the package to you, similar to how a 
	  package’s labels are designed to help the post office get your 
	  package to you.

* The next (and most important component) of a packet is the **payload**. The 
  payload refers to the actual contents of the packet. This could be an e-mail 
  message, passwords, websites, etc. 

Packets traditionally travelled between routers via wires. These wires could be 
telephone wires, television cable wires, or large fibre-optic cables running 
deep underwater. That's one of the reasons why many of the common internet 
providers were originally telephone and cable providers. 

## The dangers of information transfer on networks

In networks, there isn't a unique path that packets follow. In fact, to ensure 
that there isn't a single point of failure, several copies of each packet are 
generated, and they all travel in different directions across the network. This 
is especially true with wireless networks, where all the  computers connected 
to the wireless router sends their information through the air (similar to Mike 
TV and Wonka Vision in Willie Wonka and the Chocolate Factory). The wireless 
router, sends the information back to all the computers via the air, in a 
communication mechanism called **broadcast**. 

In broadcasting, every computer gets a perfect copy of all the packets sent 
over the network. However, since every computer knows its unique IP address, 
it discards the packets that are not addressed to it, just like you're 
supposed to discard any mail you receive that’s not addressed to you. At least, 
that's how it's supposed to work.



A malicious individual can place a special device on a network called a 
**packet sniffer**. Instead of discarding the packets that it gets, the sniffer 
stores all of them in a packet capture. You have no knowledge that a packet 
sniffer has a copy of your packets, because, of course, you get them too. It’s 
one of the consequences of being able to easily create and distribute perfect copies 
of digital content. 


![panel11](http://www.suzannejmatthews.com/images/aosk/chapter2/panel11.jpg)

## Is packet sniffing on wireless networks illegal?

Unauthorized wiretapping (putting a listening device on a wire) is illegal 
under U.S. law. However, in a wireless network there are no wires. In fact, in 
order to enable the US to spy on its enemies using radio communication, the 
wiretapping law was written in such a manner that says 
>"it shall not be unlawful under this chapter or chapter 121 of this title for 
> any person to intercept or access an electronic communication made through 
> an electronic communications system that is configured so that such electronic 
> communication is _readily accessible to the general public_ (Section 2511(2))" 

And later, 
> "_readily accessible to the general public_ means, with respect to a 
> radio communication that such communication is not scrambled or encrypted, 
> transmitted using modulation techniques." 

Thus, wiretapping secured wireless networks is illegal; but what about 
unsecured "free" WiFi hotspots? In other words, are unsecured wireless 
networks (such as those found in some homes, coffee shops, hotels, airports, 
etc.) configured in a manner that is "readily accessible to the general public"? 
And if so, is running a packet capture on it legal? 

![panel12](http://www.suzannejmatthews.com/images/aosk/chapter2/panel12.jpg)

Do you agree with Ruby's logic? Is it illegal? Remember, this question is 
different from "SHOULD it be illegal". Do people using unsecured wireless 
networks have some "expectation of privacy"? The law is currently unclear, and 
certainly groups advocate amending the Federal Wiretap Act to include a clause 
that protects wireless networks. The problem with the digital world is that 
our technology is progressing at a speed that far outpaces the laws written in 
the physical world.

Keep in mind that the exercises we are showing you in this chapter were created 
in a specially controlled environment (called a **sandbox**) so there were no 
risks in breaking the law. Since packet sniffing is a legal and ethical gray 
area, do NOT run a packet sniffer without permission on a network that you do 
not own!

(enter another scriptKitty comic here)

With all of these ethical challenges, hould packet sniffers be illegal? Why not 
just outlaw packet sniffers altogether? Isn’t packet sniffing obviously bad? 
Not exactly. 

Packet sniffers are really useful and can be use for legitimate 
purposes. For example, a company can use a packet sniffers on their own 
networks to monitor network traffic, and ensure their networks are being 
used for the correct and intended purposes, and to detect network intrusion 
attempts. They are also useful for debugging networks, and verifying the 
effectiveness of access control systems, such as spam filters and firewalls. 

![panel5](http://www.suzannejmatthews.com/images/aosk/chapter2/panel5.jpg)

Before starting the tutorial, let's go over some basic terminology and concepts:
1. **Wireshark** is a very popular packet sniffer and analyzer that has been 
around the late 1990s, and is used by many security professionals and has won 
many industrial awards. 
2. **PCAP file**: a Packet CAPture file. All data on the internet is 
transferred using packets. They contain the all information that you request 
and receive, from what you search for online, the websites you click, the 
pictures you look at. All of this information can be captured by a packet 
sniffer an stored in the PCAP file. 
from a network. 
2. **Protocol:** a set of rules that define how internet traffic is routed on 
the network. For example, if you surf the internet and search for different 
images or materials, you are using TCP (Transmission Control Protocol). If you 
would like to check your email, you will use SMTP (Simple Mail Transfer Protocol) 
or IMAP (the Internet Message Access Protocol). As another analogy, you can 
think of protocols as the box you use when you send and receive a package 
using the mail service. Depending on the content, you will use a different box, 
or for a letter you will use an envelope. 


## Packet Analysis

1. On the Pi desktop there is a folder named `Packet Sniffing`. Open the 
`capture.pcap` file found in this folder. You will notice that a program 
called Wireshark will open.
2. In Wireshark, click on the `Protocol` tab. This will sort the packets based 
on their protocols. In this tutorial we are interested in TCP/HPTP and SMTP 
traffic.
![ws1](http://www.suzannejmatthews.com/images/aosk/chapter2/ws1.png)


3. In the search tab, type `http` and press `Enter`.
4. Click on the `Info` tab. This will, again, sort the packets based on the 
information they hold. For the TCP/HTTP protocol we are interested in the 
packets that start with GET.
![ws2](http://www.suzannejmatthews.com/images/aosk/chapter2/ws2.png)


5. Scroll through the packets and see if any information looks familiar (e.g. 
websites, google searches). Take a look at the packets with `/wp-content` or 
`/search`.
6. Suppose you identified an address to a website or some words that look like 
a search. Click on the packet. In the bottom half of the screen there are 5 
categories: Frame, Ethernet II, Internet Protocol Version, Transmission 
Control Protocol, and Hypertext Transfer Protocol. In order to read what the 
packet contains, click on the arrow next to Hyper Text Transfer Protocol. If 
you look, there is an underlined text `Full request URL:` and some address. If 
you double click on that, it will open the website and you can see the content 
that the person whose packet you captured was looking for. 
![ws3](http://www.suzannejmatthews.com/images/aosk/chapter2/ws3.png)

7. Try to find as many information as you can about the owner's activity on 
the internet.


## Reliable and unreliable uniform resource locators (URLs)

![panel9](http://www.suzannejmatthews.com/images/aosk/chapter2/panel9.jpg)


![panel7](http://www.suzannejmatthews.com/images/aosk/chapter2/panel7.jpg)


![panel8](http://www.suzannejmatthews.com/images/aosk/chapter2/panel8.jpg)

1. **What makes a URL reliable?**

2. **What makes a URL unreliable?**

## Extra Exercise

1. Now that you know how to find information using the http protocol, open the 
`extra.pcap` file, go to the search tab and search for `smtp`. 
2. For this protocol we are more interested in the packets which contain `AUTH`, 
`from/to`.
3. For a packet that contains `AUTH`, in the bottom half of the screen there 
are again 5 categories: `Frame`, `Ethernet II`, `Internet Protocol Version`, 
`Transmission Control Protocol`, and `Simple Mail Transfer Protocol`. Click on 
the arrow next to `Simple Mail Transfer Protocol`. You should be able to see 
the username and password for the mail account
4. For a packet that contains `FROM/ TO` there is a 6th category: `Internet 
Message Format`. Click on the arrow next to it and from the new categories, 
click on the arrow next to Line-based text data. This reveals the content of 
the email that has been received or sent. 
5. Try to see if you can read the emails.


##Protecting Yourself Against Packet Sniffers
So how do we protect ourselves against packet sniffing? The answer is not to 
simply use password protected wireless networks. Someone who is intent on 
stealing your data will likely break the password. Once they are in the 
network, they can then run the packet sniffer and your information will be lost.
So what do we do? The answer is to use encryption whenever possible!

(add script kitty comic about how we know when encryption is on!)

Encryption algorithms are based on really hard computer science problems 
that will take an incredibly long time to brute force. Consequently, 
this is considered the only truly “safe” way to transmit packets. Banks, online 
stores, and other entities that deal with financial transactions on a regular 
basis encrypt the packets being sent to them. That is why you always connect to 
an https address with them.

There have been several high profile cases involving packet sniffing that has 
occurred in decade. You can read more about them at the end of this tutorial. 
However, one of the positive outcomes of these highly public cases is that a 
lot of websites are using encryption by default. 

(enter scriptkitty comic about how we know if encryption is on?)

An easy way to check if your connection is encrypted is to look at the URL. 
If it starts with "https://" that means it is encrypted. In browsers such as 
Chrome, look for the little green lock and the words "secure". That lets us 
know that encryption is on.


(enter scriptkitty comic asking if encryption is guaranteed to keep our
information safe)

Keep in mind that if someone really wants to steal your information, they 
will try hard. There are a lot of malicious actors who are actively trying to 
look for vulnerabilities in TLS (the security layer that defines https), and 
vulnerabilities are found.

Keep in mind that connecting to a site using encryption only protects your data 
as it is in transit to that site. If a site is hacked, or if the owners of the 
website decides to share your information with third parties, your personal 
information can still be compromised.

## Protecting your data

The surest way to ensure that your data never gets stolen on the internet is 
to not use the internet. But, of course, this is not a reasonable or feasible 
course of action! To maximize the security of your personal data, follow these 
good essential tips.

1. **Never share anything online that you don't want everyone knowing**. Be 
   careful about what information you share on social media. This is not 
   limited to text! Since perfect copies can be made of all digital content, 
   be cautious about what photos and videos you upload or share as well.

2. **Regularly Check your Social Media Security Settings**. Lock down your 
   social media accounts so that only real friends (aka, people you know in 
   real life) can access them. Some websites reset your security settings on 
   updates, so it is a good idea to periodically check and ensure that they are 
   where you want them to be. Be sure to read the Terms of Service (TOS) of 
   whatever social media site you use. Nothing online is truly free -- understand 
   who owns and how they may use your data!

3. **Reduce your social media footprint**. Be careful on which "friend" requests 
   you accept, and who is following you on twitter. Turn off GPS location posting 
   on social media. If people know that you are in Hawaii, they know you aren't 
   home! Remember, once it is online your information is there forever! It is 
   extremely hard to remove content from the internet once it is there. 

4. **Use encryption whenever possible.** Use https as much as possible when you 
   search the web. Consider turning on encryption on your phone, laptop, or 
   other devices you may own. 
   
![panel3](http://www.suzannejmatthews.com/images/aosk/chapter2/panel13.jpg)   




