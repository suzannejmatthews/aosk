
# Intro

In the previous chapter we used Wireshark to recreate a transfered file and we used John the Ripper to break its password.
In this chapter we introduce the idea of remote controling using ssh and what password reuse can cause.

##  What is password reuse and what are its implications?

A user usually has accounts on different websites (facebook, gmail, udacity, etc.). It becomes complciated to remember all the passwords especially when the account is not often used or if the user never logs out (ie. always logged in on facebook). A common method is to use the same password for every account. This approach is called password reuse. While it makes memorizing the passwords less complicated, it represents a major security problem. When someone discovers one of your passwords, chances are that that person will try the same password for other accounts that you have. In this situation, each account that has this password will be compromised. The result is called daisy chaining. 

You do not want someone to have access to eveything you own if they discovered one of your passwords, right? What can you do? We provide some tips at the end of the tutorial.


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

## What did we learn from this chapter?

After finding one of the passwords that Gerry had on a file, we assumed that he used the same passwords for his accounts. We used SSH to try to get access to his account. The password seems to work. The lesson with this chapter is that password reuse is always a bad idea. Anyone that can access your accounts can extract sensitive information and use them in your disadvantage. 

## Tips for good password management
1. **Take the password requirements seriously**. Remember how annoying some websites are when they ask for a complicated password that you will never remeber? It may be annoying but it is for your own security. Having a long password composed of lowercase, upercase letters, symbols, and numbers mixed, increases the complexity of the password. Hence, it becomes harder for an attacker to discover it. Even in the situation where your password is discovered, it will look like a random string of characters. The attacker will have a hard time discovering your password. It is not impossible, but very unlikely.
2. **Use a password manager**. There are different tools on the internet that manage your passwords. They change your passwords frequently with randomly generated strings. All your passwords are available to you only. Not even the people who maintain the application do not have access to your passwords. 
3. **Use a password generator**. Similarly to the password managers, the internet has password generators available. These tools provide a random password that you can use. In this case, you might want to write your passwords in a notebook or in some hidden and password protected file. 
4. **Change your passwords frequently**. A complicated password does not imply that it cannot be cracked. It takes more time, but it is possibly. This is the reason why changing passwords regularly becomes important. When changing a password, do not use a password that has similarities with the old one (ie. old password: book123, new password: book1122).
5. **Use two factor authentication where it is available**. Most websites offer this option nowadays. This requires two methods of authentication in order to access that account. For example, you can set up your account to ask for a password from the keyboard, and then to ask for a pin number introduced from your phone. In this way if someone discovers your password, that person will not be able to access the account without the pin code. This is also usefull for notifications. If your phone asks for the pin number and you know you are not the one who introduced the password, you can immediately take action and change your password.  
