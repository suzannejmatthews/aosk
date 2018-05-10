
# Intro

In the previous chapter we used Wireshark to recreate a transfered file and we used John the Ripper to break its password.
In this chapter we introduce the idea of remote controling using ssh and what password reuse can cause.


## What is daisy-chain authentication?
  
This term defines an attacker who uses simple and not very complicated technical skills in order to break into an account. A lot of times this is accomplished by doing some reasearch about the target. This type of attacks are challenging to protect against and detect since they do not involve breaking someone's security. For example, an attacker gathers as much information as possible from social media or other places. Now the attacker can try to guess some passwords, or to answer the security questions in the password recovery process for an account. None of these methods will trigger any intrusion detection system. Collecting information about someone has become easier with all the social media websites. 

Password reuse plays an important role in the daisy-chaining attack. Cosnidering that using the simple methods described above, an attacker manages to access one of your accounts. Since finding this password was not hard, the attacker would assume that all your passwords have a low level of security. If you as the user use the same password on multiple accounts, once one of them is found, all accounts can be compromised. Again, no intrusion detection system would be triggered since the attacker acts as the owner of the accounts. 
To understand the extent to which daisy-chaining can go, look for *Mat Honan's Epic Hacking*. This real story presents a situation where just an email and a physicall address can be dangerous. Note that the attacker did not use any complicated techniques.

In order to decrease the chance of such an attack, many companies use identity assurance (IA) - process that confirms that the person trying to connect to an account is truly the owner. In IA the credentials provided for identification varry from personal information to a username and a digital certificate. After providing the credentials, the IA will provide a certainty related to the true identity of the user who sends the credentials. The degree of certainty is known as the assurance level and it has 4 possible levels. Usually, this service is provided through some companies and it is not free.


## What is SSH?

SSH stands for Secure Socket Shell. It is a protocol that allows a user to remote control a computer. It provides a secure communication between the computers connecting. This protocol is usually used by the network administrators for managing computers remotely. Even if your network is not the best in terms of security, SSH offers an extra layer of encryption. Most of the operating systems come with SSH already installed. There are programs that offer a graphical interface for SSH so the user does not have to use the command line. A software like this is WinSCP. SSH can also be used to transfer files. It uses the SFTP (SSH File Transfer Protocol) for transfer.


## Steps for this tutorial

In this tutorial we are going to try to log in Gerry's computer via ssh and see if he made the mistake of using the same password in multiple places. 

1. Open a command prompt in your desktop
2. Now, we know that Gerry's username for his account is gerry. We will try to ssh into this. Type the following command `ssh gerry@linx12345`. After typing this command, we are required a password. Let's try to see if the password discovered in the previous chapter works. Note: If you did not finish chapter 3, we highly encourage you do so.

![ssh](http://www.suzannejmatthews.com/images/aosk/chapter4/SSH.PNG)

3. Type the password from the previous chapter and press enter. If the password works, you should be connected to Gerry's account. 
4. We will not have a graphical interface here, so we have to work with the command line. Type `ls and press enter`. You should see all the files Gerry has on his desktop.

![ls](http://www.suzannejmatthews.com/images/aosk/chapter4/ls.PNG)

5. It looks like there is a file called `meeting.txt`. Let's see if there is some useful information in there. Type `cat meeting.txt`. In the command prompt you will see the content of the file.

![Cat](http://www.suzannejmatthews.com/images/aosk/chapter4/Cat.PNG)

6. Interesting! It looks like the file has some coordinates. Try to see where the coordinations point. Google maps may be useful. 
7. To exit the SSH session, you can type in the terminal, `logout`

## What did Gerry do wrong?

As we saw in the previous chapters Gerry found the pet adoption website and contacted their customer service. The email he received included some concerning details. The person was asking for bank account details, the address from which the email was sent looked far from some official address, and the catalog was available only after contacting the customer service. Gerry was actually "cat(ph)fished". 
Usually the term phishing refers to an attacker sending multiple malicious emails to a target in order to induce the target to provide sensitive information. Catphising is a variation of this practice. This attack usually takes advantage of someone's interests. In our case, an attacker could see that Gerry was looking to adopt a cat. Based on this information, the attacker created a fake email address and pretended to be the adoption store. When Gerry seemed interested in adopting a cat, the attacker tryes to persuade Gerry to send sensitive information. 
For our tutorials, this is a story, but it has applicability in real life. One should always check twice before doing any action on the internet.



## Tips for good password management

1. **Use a password manager**. There are different tools on the internet that manage your passwords. They change your passwords frequently with randomly generated strings. All your passwords are available to you only. Not even the people who maintain the application do not have access to your passwords. 
2. **Use a password generator**. Similarly to the password managers, the internet has password generators available. These tools provide a random password that you can use. In this case, you might want to write your passwords in a notebook or in some hidden and password protected file. 
3. **Change your passwords frequently**. A complicated password does not imply that it cannot be cracked. It takes more time, but it is possibly. This is the reason why changing passwords regularly becomes important. When changing a password, do not use a password that has similarities with the old one (ie. old password: book123, new password: book1122).
4. **Use two factor authentication where it is available**. Most websites offer this option nowadays. This requires two methods of authentication in order to access that account. For example, you can set up your account to ask for a password from the keyboard, and then to ask for a pin number introduced from your phone. In this way if someone discovers your password, that person will not be able to access the account without the pin code. This is also usefull for notifications. If your phone asks for the pin number and you know you are not the one who introduced the password, you can immediately take action and change your password.  
