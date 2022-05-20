# The Ghost in the Wire

![panel1](http://www.suzannejmatthews.com/images/aosk/chapter2/panel1.jpg)

Gerry swung the door open wide, and marched in like on a mission, immediately 
sitting down at the desk and turning on the computer. 
"I wonder what Gerry's up to?" Ruby pondered. "What if Gerry's looking at cats again!?!"
Ruby walked over to Gerry's computer to take a look, but she couldn't quite 
see what was going on. Her curiosity got the best of her.


![panel2](http://www.suzannejmatthews.com/images/aosk/chapter2/panel2.jpg)

As Ruby scurried to her room, by pleasant surprise, Pixel fluttered in through the window.

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
anything learned in this tutorial outside of the Raspberry Pi. -->

## How is Information Sent on the Internet?

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

* The next (and most important) component of a packet is the **payload**. The 
  payload refers to the actual contents of the packet. This could be an e-mail 
  message, passwords, websites, etc. 

Packets traditionally travelled between routers via wires. These wires could be 
telephone wires, television cable wires, or large fiber-optic cables running 
deep underwater. That's one of the reasons why many common internet 
providers were originally telephone and cable providers. 

## The Dangers of Information Transfer on Networks

In wireless networks, all the computers connected to a wireless router send their 
information through the air (similar to Mike Teavee and Wonka Vision in Willy Wonka 
and the Chocolate Factory). The wireless router sends the information back to all the 
computers via the air in a communication mechanism called **broadcast**. 

In broadcasting, each computer gets a perfect copy of all the packets sent 
over the network, but only keeps the ones that are addressed to it.  Just like you're 
supposed to discard any mail you receive that’s not addressed to you. That's how it's 
_supposed_ to work, at least.

A malicious individual can place a special device on a network called a 
**packet sniffer**. Instead of discarding the packets that a computer gets, the sniffer 
stores all of them in a packet capture. You have no knowledge that a packet 
sniffer has a copy of your packets, because, of course, you get them too. It’s 
one of the consequences of being able to easily create and distribute perfect copies 
of digital content. 

For more information on networks and packets, click [here](chapter2advanced.md).

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
etc.) configured in a manner that is "readily accessible to the general public?" 
And if so, is running a packet capture on it legal? 

![panel12](http://www.suzannejmatthews.com/images/aosk/chapter2/panel12.jpg)

Do you agree with Ruby's logic? Is it illegal? Remember, this question is 
different from asking whether it SHOULD be illegal. Do people using unsecured wireless 
networks have some "expectation of privacy?" The law is currently unclear, and 
there are groups who advocate for amending the Federal Wiretap Act to include a clause 
that protects wireless networks. The problem with the digital world is that 
our technology is progressing at a speed that far outpaces the laws written in 
the physical world.

Keep in mind that the exercises we are showing you in this chapter were created 
in a specially controlled environment (called a **sandbox**) so there were no 
risks in breaking the law. Since packet sniffing is a legal and ethical gray 
area, you should NOT run a packet sniffer without permission on a network that you do 
not own!

Considering all of these ethical challenges, shouldn't packet sniffers be illegal? 
Isn’t packet sniffing obviously bad? 
Not exactly. 

Packet sniffers are really useful and can be used for legitimate 
purposes. For example, a company can use a packet sniffers on their own 
networks to monitor network traffic, and ensure their networks are being 
used for the correct and intended purposes, and to detect network intrusion 
attempts. They are also useful for debugging networks, and verifying the 
effectiveness of access control systems, such as spam filters and firewalls. 

![panel5](http://www.suzannejmatthews.com/images/aosk/chapter2/panel5.jpg)

Before starting the tutorial, let's go over some basic terminology and concepts:
1. **Wireshark** is a popular packet sniffer and analyzer

2. **PCAP file**: a Packet CAPture file. Contains all of the information captured 
by a packet sniffer over a period of time

3. **Protocol:** a set of rules that define how internet traffic is routed on the network


## Packet Analysis

1. On the Pi desktop there is a folder named `Packet Sniffing`. Open the 
`capture.pcap` file found in this folder. You will notice that a program 
called Wireshark will open.

2. In Wireshark, click on the `Protocol` tab. This will sort the packets based 
on their protocols. In this tutorial we are interested in TCP/HPTP,SMTP, and FTP  
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

7. Try to find as much information as you can about Gerry's activity on 
the Internet.

Now that we found some information about Gerry's searches on the Internet, we will try to find some other unencrypted data.

8. Go to the search tab and search for `smtp`. For this protocol we are more interested in the packets which contain
`from/to`. Click on the `info` tab to sort the packets. 
![smtp](http://www.suzannejmatthews.com/images/aosk/chapter2/SMTP.PNG)

9. For a packet that contains `FROM/ TO` there is a 6th category: `Internet 
Message Format`. Click on the arrow next to it and from the new categories, 
click on the arrow next to Line-based text data. This reveals the content of 
the email that has been received or sent. 
  To read the content, an alternative solution is to `right-click on the packet -> Follow -> TCP Stream`.
 
![content](http://www.suzannejmatthews.com/images/aosk/chapter2/content.PNG)

Hmm...what is Gerry planning?


## Reliable and unreliable uniform resource locators (URLs)

![panel9](http://www.suzannejmatthews.com/images/aosk/chapter2/panel9.jpg)


![panel7](http://www.suzannejmatthews.com/images/aosk/chapter2/panel7.jpg)


![panel8](http://www.suzannejmatthews.com/images/aosk/chapter2/panel8.jpg)

1. **What is a uniform resource locator (URL)?**
A URL is a protocal for identifying addresses on the internent. It's what you 
type into the address bar to navigate to a website. An example of a URL would be 
`https://www.google.com` the URL for Google.

2. **What makes up a URL?**
Looking at a URL, after the `www.` the domain name can be found. For example, 
in the URL `www.google.com`, google.com is the domain name. This is often times
where the name of the website or organization affiliated with that website is 
located. Within the domain name is the domain suffix. In the example above the 
domain suffix is the **.com**. Domain suffixes come in quite the variety including, 
**.com**, **.net**, **.gov**, **.org**, **.edu**, **.mil** and many more. Though the 
suffix usually refers to the type of organization who created the website, that is 
not always true. Websites can register with any domain suffix, thus it is recommended 
to still check the website to ensure it actually aligns with its domain suffix. <sup>1</sup>. 

3. **What makes a URL unreliable?**
URLs with abstract numbers and symbols often give insight that the site may not be 
the most reliable or safe. Also inspect the domain name, if it says something to good
to be true, it probably is, like "freemoney.com". If you ever question whether or not
a website is safe, there are sites like <a>http://www.urlvoid.com/</a> which check 
the reputation of websites and report back fradulent and malicious websites. 
Malicious websites have the capabilities to infect your computer, so be careful.<sup>2</sup>.


## Protecting Yourself Against Packet Sniffers
So how do we protect ourselves against packet sniffing? The answer is not to 
simply use password protected wireless networks. Someone who is intent on 
stealing your data will likely break the password. Once they are in the 
network, they can then run the packet sniffer and your information will be lost.
So what do we do? The answer is to use encryption whenever possible!

Encryption algorithms are based on really hard computer science problems 
that will take an incredibly long time to brute force. Consequently, 
this is considered the only truly “safe” way to transmit packets. Banks, online 
stores, and other entities that deal with financial transactions on a regular 
basis encrypt the packets being sent to them. That is why you always connect to 
an https address with them.

![panel16](http://www.suzannejmatthews.com/images/aosk/chapter2/panel16.JPG)

An easy way to check if your connection is encrypted is to look at the URL. 
If it starts with "https://" that means it is encrypted. In browsers such as 
Chrome, look for the little green lock and the words "secure". That lets us 
know that encryption is on.

![panel15](http://www.suzannejmatthews.com/images/aosk/chapter2/panel15.JPG)

Remember that if someone really wants to steal your information, they 
will try hard. There are a lot of malicious actors who are actively looking for 
vulnerabilities in TLS (the security layer that defines https).

Keep in mind that connecting to a site using encryption only protects your data 
as it is in transit to that site. If a site is hacked, or if the owner of the 
website decides to share your information with third parties, your personal 
information can still be compromised.

## Protecting Your Data

The most reliable way to ensure that your data never gets stolen on the internet is 
to not use the internet. But, of course, this is not a reasonable or feasible 
course of action! To maximize the security of your personal data, follow these essential tips.

1. **Never share anything online that you don't want everyone knowing**

2. **Regularly Check your Social Media Security Settings**

   <!--Find image of weird social media requests, or visual example of oversharing-->

3. **Reduce your social media footprint**

4. **Use encryption whenever possible**

For more details on protecting your data online, click [here](protectdata.md)!

![panel3](http://www.suzannejmatthews.com/images/aosk/chapter2/panel13.jpg)   

<sup>1</sup>. “Evaluating Information - STAAR Method: URL & What It Can Tell You.” 
University of South Carolina Upstate Library, 8 Feb. 2018, 
<a>http://uscupstate.libguides.com/c.php?g=257977&p=1721715.</a>

<sup>2</sup>. Phelps, Justin. “How to Tell If a Link Is Safe Without Clicking on It.” 
PCWorld, 7 Feb. 2012, 11:31 am, 
<a>www.pcworld.com/article/248963/how_to_tell_if_a_link_is_safe_without_clicking_on_it.html.</a>

[Click here]("chapter3.md") to go to the next chapter. 
