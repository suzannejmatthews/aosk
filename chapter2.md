# The Ghost in the Wire

background information

## Purpose and basic terminology

The purpose of this tutorial is to show the students how vulnerable they can be 
on an unsecured network. While it is fun and interesting to read emails, find 
passwords and see what anyone else is searching, it is important to mention 
that this tutorial is performed in a secure environment and the network 
packets are specifically created for this activity. The legality of capturing 
and inspecting packets is a gray area and thus, you should not attempt to do 
anything learn in this tutorial outside of the Raspberry Pi.

Before starting the tutorial, let's go over some basic terminology and concepts:
1. **PCAP file**: a Packet CAPture file. When you are accessing the internet, 
whether you search for different things, you access a specific website or you 
send an email, everything is transferred using packets. They contain the 
information that you request and receive. This file contains captured packets 
from a network. 
2. **Protocol:** a set of rules that allow the internet traffic. Depending on 
what you do on the internet, there are multiple protocols used. For example, 
if you surf the internet and search for different images or materials, you are 
using TCP (Transmission Control Protocol). If you would like to check your 
email, you will use SMTP (Simple Mail Transfer Protocol). You can think of 
protocols as the box you use when you send and receive a package using the 
mail service. Depending on the content, you will use a different box, or for a 
letter you will use an envelope. 
3. **Wireshark:** a powerful application that allows the user to capture and 
analyze internet packets. It is easy to use and very user-friendly.

## Packet Analysis

1. On the Pi desktop there is a folder named `Packet Sniffing`. Open the 
`capture.pcap` file found in this folder. You will notice that a program 
called Wireshark will open.
2. In Wireshark, click on the `Protocol` tab. This will sort the packets based 
on their protocols. In this tutorial we are interested in TCP/HPTP and SMTP 
traffic.
3. In the search tab, type `http` and press `Enter`.
4. Click on the `Info` tab. This will, again, sort the packets based on the 
information they hold. For the TCP/HTTP protocol we are interested in the 
packets that start with GET.
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
7. Try to find as many information as you can about the owner's activity on 
the internet.

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

Note: Nowadays, most email services are encrypted. Therefore you will not be 
able to read the content as simple as in this tutorial. 






