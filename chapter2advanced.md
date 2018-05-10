# Advanced Networks and Information Transfer

## Network Fundamentals
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

## The Dangers of Information Transfer on Networks

In networks, packets don't follow one unique path. In fact, to ensure 
that there isn't a single point of failure, several copies of each packet are 
generated, and they all travel in different directions across the network. This 
is especially true with wireless networks, where all the  computers connected 
to the wireless router send their information through the air (similar to Mike 
Teavee and Wonka Vision in Willy Wonka and the Chocolate Factory). The wireless 
router sends the information back to all the computers via the air in a 
communication mechanism called **broadcast**. 

In broadcasting, every computer gets a perfect copy of all the packets sent 
over the network. However, since every computer knows its unique IP address, 
it discards the packets that are not addressed to it. Just like you're 
supposed to discard any mail you receive that’s not addressed to you. At least, 
that's how it's supposed to work.

A malicious individual can place a special device on a network called a 
**packet sniffer**. Instead of discarding the packets that it gets, the sniffer 
stores all of them in a packet capture. You have no knowledge that a packet 
sniffer has a copy of your packets, because, of course, you get them too. It’s 
one of the consequences of being able to easily create and distribute perfect copies 
of digital content. 

## Basic Terminology and Concepts

1. **Wireshark** is a very popular packet sniffer and analyzer that has been 
around the late 1990s, and is used by many security professionals and has won 
many industrial awards. 

2. **PCAP file**: a Packet CAPture file. All data on the internet is 
transferred using packets. They contain the all information that you request 
and receive, from what you search for online, the websites you click, the 
pictures you look at. All of this information can be captured by a packet 
sniffer an stored in the PCAP file. 
from a network. 

3. **Protocol:** a set of rules that define how internet traffic is routed on 
the network. For example, if you surf the internet and search for different 
images or materials, you are using TCP (Transmission Control Protocol). If you 
would like to check your email, you will use SMTP (Simple Mail Transfer Protocol) 
or IMAP (the Internet Message Access Protocol). As another analogy, you can 
think of protocols as the box you use when you send and receive a package 
using the mail service. Depending on the content, you will use a different box, 
or for a letter you will use an envelope.




To go back to the chapter, click [here](chapter2.md).

