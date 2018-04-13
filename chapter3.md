
# Intro

In the previous tutorial we used Wireshark to look for unencrypted information. If you skipped it, we **highly encourage** that you go back and complete it, as it explains basic concepts of Wireshark. In this chapter, we will use Wireshark to recreate a transfered password-protected file and then break its password so that we can see the content. 


# How do passwords work?

If you have any online accounts, you are probably familiar with the concept of a password. A _password_ is a phrase or sequence of characters that is associated with an account. To ensure that the 
correct person accesses an account online, websites _authenticates_ the person logging in by checking first if the inputted username matches a username on record, and if a match is found, if the 
inputted password matches the password stored along with username.

In the early days of the internet, username and password information were stored in human-readable form called plain-text. These files look like the following:
```
edishungry:password123
aeropixel:racecars
rubycat:scriptkitty
```

In the above file, `edishungry` is an example of a username. This user's asosciated password is `password123`. Similarly, `aeropixel`'s password is `racecars`. As you can imagine, storing passwords like this 
is not very secure. Even if a user chooses a strong password, if the company that owns the server stores the passwords in plaintext, a hacker that gets ahold of the above file would know all the 
usernames and passwords on the system!

To increase security, most companies _hash_ passwords before they are stored along with usernames. A hashed password commonly looks like a long string of random text. So, the corresponding 
hashed password file may look something like:

```
edishungry:482c811da5d5b4bc6d497ffa98491e38
aeropixel:1d615366645ce4a7640755a6f7ad9746
rubycat:13c9a04541cd023982a03b00c8c5e9ea
```

In reality, those long strings are examples of _hashes_. To create a hash, one must use a hash function. In the above example, the password hashes are produced by a hash function called MD5. The MD5 
hash function is _assymetric_ -- that is, it cannot be reversed. If we run the same string through MD5 multiple times, we will get the same hash. However, entering two different strings (no matter how 
similar they may be) will _almost always_ result in a different string. We say "almost always" because it is possible wtih very low probability. 

## Try it out yourself!
Open the terminal and type the command `echo -n 'scriptkitty' | md5sum`:

```
> echo -n 'scriptkitty' | md5sum
13c9a04541cd023982a03b00c8c5e9ea
```

Run the command multiple times. You will see that you always get the same hash. Now try changing `scriptkitty` to `racecars`. Do you get the same hash associated with the username `aeropixel`? If you 
typed it in correctly, you should!

When Ruby types in her username (`rubycat`) into our imaginary website, the server will hash her inputted password using MD5, and compare it with the stored hash associated with the account `rubycat`.
If the hashes match, the website wlil authenticate Ruby. 

While your password can usually be anything you want, some passwords are better than others. As we will see in this tutorial, simple or "weak" passwords are easily guessed. Likewise, while using hashes 
is always better than using plaintext, some hash functions are better than others. MD5 (which was widely used in earlier days) is now no longer considered secure. 


# What is FTP and how does it work?
When we want to transfer a file from one computer to another over the internet, we use the File Transfer Protocol (FTP). This protocol is a set of rules specially created so that a client can retrieve files from a server. FTP has two different standards: one for control (FTP) and one for data (FTP-DATA). The control version establishes the connection, verifies the username and password (not mandatory), and establishes which file is requested. FTP-DATA, then, takes care of transfering the requested file. 

As any other data on the internet, the file will be sent in multiple packets depending on its size. FTP protocol is widely used due to its simplicity. However, the downside is that it is not secure. In general, simple FTP is used for educational purposes or to transfer files between trusted entities in a private network. In order to eliminate this security problem, FPT is secured with Secure Sockets Layer(SSL) or Transport Layer Security(TLS) and in this way it becomes FTPS. 

__Note__: In general it is safe to assume that the "S" at the end of a protocol means that the protocol is secured (i.e. HTTPS, FTPS, IPS)

# Recreate the file

1. Open the .pcap file provided and type in the filter bar FTP. Now, you can see the authentication credentials, and the name of the requested file

2. We are interested in __Catalog.rar__. Type in the filter bar FTP-DATA. Right click on any packet and select folow TCP stream. The window that opens shows how the tranfered file looks in ASCII format. These random characters represent how the file is contructed in memory. 
![followStream](http://www.suzannejmatthews.com/images/aosk/chapter3/ftp-followStream.PNG)
	 
3. Go to the `Show and save data as` field and select `Raw`. Click on `Save as`
![changeToRaw](http://www.suzannejmatthews.com/images/aosk/chapter3/ftpStreamChangeToRaw.PNG)
	
4. In the new window, double click on `Desktop1`, and write `captured.rar` in the Name field and click on `Save`.
![Save](http://www.suzannejmatthews.com/images/aosk/chapter3/SaveTheFileFromShark.PNG)
	
5. Check on your Pi's desktop. You should see the captured.rar file
 
 Since this file is a an archive (.rar) we have to unrar it. An archive is a way to compress a larger file into a smaller one. There are different tools for this. The most common are: RAR, ZIP and tar.gz. So if you have a file of the following formats, name.zip, name.rar, name.tar.gz, it means that you have to decompress it in order to acces the content.

6. Right click on Desktop and open a terminal. To unrar our file we will use `unrar e captured.rar` 
![unrar](http://www.suzannejmatthews.com/images/aosk/chapter3/Unrar.PNG)
  
  Oh oh! We have a problem. We have to insert a password but we do not know anything about it. Wouldn't be great if there was a tool to help us break this password? 
  
  It is our lucky day! There is a tool and it is called John the Ripper.
  
# What is John the Ripper?
John the Ripper is a software tool used for password cracking. It is free and runs on the most common operating systems (i.e Windows, Linux, MacOS, Ubuntu). There is a free version of this software, which is frequently used. If the user needs an enhanced version of this software, there are available versions for purchase.


## What is a rainbow table?
You can use WinRTGen to create your own rainbow table. A **rainbow table** is essentialy a special wordlist that you create for a specific type of hash. Since in the previous years, the passwords have been improved, the common wordlist will probably fail, assuming that a person does not uses simple passwords anymore. Generating a new rainbow table requires a good computer configuration, depending on how big the table would be and the type of hash used. 

## How does John the Ripper work?
John the Ripper brings many password crackers and hash types detectors in one package. In general, John cracks weak hashes. There are two types of attacks attached to John. The dictionary attack takes string samples, usually from a wordlist (dictionary) containing passwords cracked before, encrypts them in the same format as the password being checked and compares the output to the password. The second type of attack is the brute force attack. For this one, John goes through all the possible plaintexts, hashes and compares them to the given password. One useful tool for this attack is the character frequency table. If the password contains more frequently used characters then it would take less time to crack the hash. This method is useful when the password is not in found in wordlists. The downside is the longer runtime.

In this tutorial we will use John the Ripper to crack the password of a .rar file, using a dictionary attack.

## How do I use John the Ripper to find the password for our file?

1. Open a terminal on your destkop. Type `rar2john captured.rar > hashed_password.txt`. Press Enter. This command tells John the Ripper that we have a .rar file with a password and we want its hash written on _hashed_password.txt_.
![rar2john](http://www.suzannejmatthews.com/images/aosk/chapter3/rar2john.PNG)

2. If you look on your desktop you can see that you have a *hashed_password.txt* file. If you want to see what it contains, you can type `less hashed_password.txt`. Those characters and numbers represent the hash for our password. Press `q` when you want __to return__ to the terminal. 

3. Now is the time to find our password. In the terminal, type `john --wordlist=/usr/share/john/password.lst hashed_password.txt`. Press Enter.
![cracked](http://www.suzannejmatthews.com/images/aosk/chapter3/CrackedPassword.PNG)
	
   Let's look at this command. John the Ripper needs a wordlist(dictionary) for this attack. `--wordlist=/usr/share/john/password.lst` tells John to use the _password.lst_ file located at `/usr/share/john/password.lst`. If you want to use a different wordlist, you can change the location and John will take care of the rest. Then, we passed in the file containing the hash. John will use the wordlist and the hash and will find the one password that matches the hash.

4. Back in the terminal. Type `john --show hashed_password.txt`. This command will show you the word that corresponds to the hash. __This is our password.__
![show](http://www.suzannejmatthews.com/images/aosk/chapter3/ShowPassword.PNG) 
	

## What did Gerry do wrong?
As we saw in the e-mail, the "consultant" from the pet store has some pretty concerning requests ( only $20 bills, he will establish the place, asks for card information). Moreover, they do not simply send the catalog via email, but ask for an FTP connection.
Unless you know and trust the sender and it is necessary, do not use a simple FTP connection for transferring files. Anyone connected on that network can capture the traffic and recreate it. Yes, it is illegal, but we it is better to protect ourselves. 

In the second part of this tutorial, we saw how a simple password can be found very quick. Using simple passwords is never recommended. Words that can be found in a dictionary or combinations that use the same symbols are easy to be cracked nowadays. 

## How can we protect oursevles?
1. For file transfer, use trusted websites, or directly an e-mail attachement. Anything that requires an unsecured connection should be a sign for a possible threat. 
2. When creating passwords, it is recommended to use different combinations of characters. A relatively strong password will look like a random combination (i.e @[Ot2dP5Li9C%B}r ). 
3. Do not use the same passwords for different accounts. In this way, even if one of your accounts is compromised, your other accounts will not be in danger.
4. If keeping track of strong passwords seems hard, you can use a password manager. There are plenty of them for free on the internet (be careful from what webiste you download it). These tools generate and store strong passwords for you.
5. If it is mandatory for you to send important information through e-mail, use encryption tools so that you can add more encryption layers, and a safe method of transferring files.


