
Intro

In the previous tutorial we used Wireshark to look for unencrypted information. If you skiped it, I highly encourage that you complete it as it shows some basic knowledge about Wireshark. In chapter 3 we are using Wireshark to recreate a transfered file and then break its password so that we can see the content. 


Recreate the file
When we want to transfer a file from a computer to another over the internet we use the File Transfer Protocol (FTP). This protocol is a set of rules specially created so that a client can retrieve files from a server. FTP has two different standards: one for control (FTP) and one for data (FTP-DATA). The control version establishes the connection, verifies the username and password (not mandatory), and establishes which file is requested. FTP-DATA, then, takes care of transfering the requested file. As any other data on the internet, the file will be sent in multiple packets depending on its size. FTP protocol is widely used due to its simplicity. However, the downside is that it is not secure. In general, simple FTP is used for educational purposes or to transfer files between trusted entities in a private network. In order to eliminate this security problem, FPT is secured with Secure Sockets Layer(SSL) or Transport Layer Security(TLS) and in this way it becomes FTPS. 

*Note: In general it is safe to assume that the "S" at the end of a protocol means that the protocol is secured (i.e. HTTPS, FTPS, IPS)

1. Open the .pcap file provided and type in the filter bar FTP. Now, you can see the authentication credentials, and the name of the requested file

2. We are interested in "Catalog.rar". Type in the filter bar FTP-DATA. Right click on any packet and select folow TCP stream. The window that opens shows how the tranfered file looks in ASCII format. These random characters represent how the file is contructed in memory. 
     {insert ftp-follow stream.PNG here}
	 
3. Go to the "Show and save data as" field and select "Raw". Click on "Save as"
	{insert ftp stream change to raw.PNG here}
	
4. In the new window, double click on "Desktop", write "captured.rar" in the Name field and click on "Save".
	{insert save the file from shark.PNG here}
	
5. Check on your Pi's desktop. You should see the captured.rar file
 
 Since this file is a an archive (.rar) we have to unrar it. An archive is a way to compress a larger file into a smaller one. There are different tools for this. The most common are: RAR, ZIP and tar.gz. So if you have a file of the following formats, name.zip, name.rar, name.tar.gz, it means that you have to decompress it in order to acces the content.

6. Right click on Desktop and open a terminal. To unrar our file we will use "unrar e captured.rar" 
	{insert Unrar.PNG here}
  Oh oh! We have a problem. We have to introduce a password but we do not know anything about it. Wouldn't be great if there was a tool to help us break this password? 
  
  It is our lucky day. There is a tool and it is called John the Ripper.
  
What is John the Ripper?
John the Ripper is a software tool used for password cracking. It is free and runs on the most common operating systems (i.e Windows, Linux, MacOS, Ubuntu). There is a free version of this software, which is frequently used. If the user needs an enhanced version of this software, there are available versions for purchase.

Passwords are not stored in plain text. They are encrypted using asymmetric hash functions. A hash is a function that transforms the input into an encoded string of characters with fixed length. The function behaves like a normal mathematical function, transforming the input. The difference is that a hash function makes the reverse impossible unless the function is known. A common attack on such an encryption is a rainbow table. 

You can use WinRTGen to create your own rainbow table. A rainbow table is essential a special wordlist that you create for a specific type of hash. Since in the previous years, the passwords have been improved, the common wordlist will probably fail, assuming that a person does not uses simple passwords anymore. Generating a new rainbow table requires a good computer configuration, depending on how big the table would be and the type of hash used. 

John the Ripper brings many password crackers and hash types detectors in one package. In general, John cracks weak hashes. There are two types of attacks attached to John. The dictionary attack takes string samples, usually from a wordlist (dictionary) containing passwords cracked before, encrypts them in the same format as the password being checked and compares the output to the password. The second type of attack is the brute force attack. For this one, John goes through all the possible plaintexts, hashes and compares them to the given password. One useful tool for this attack is the character frequency table. If the password contains more frequently used characters then it would take less time to crack the hash. This method is useful when the password is not in found in wordlists. The downside is the longer runtime.

In this tutorial we will use John the Ripper to crack the password of a .rar file, using a dictionary attack.

How do I use John the Ripper to find the password forour file?

1. Open a terminal on your destkop. Type " rar2john captured.rar > hashed_password.txt". Press Enter. This command tells John the Ripper that we have a .rar file with a password and we want its hash written on hashed_password.txt.
	{insert rar2john.PNG here}

2. If you look on your desktop you can see that you have a hashed_password.txt file. If you want to see what it contains, you can type "less hashed_password.txt". Those characters and numbers represent the hash for our password. Press "q" when you want to return to the terminal. 

3. Now is the time to find our password. In the terminal, type "john --wordlist=/usr/share/john/password.lst hashed_password.txt". Press Enter.
	{ insert Cracked Password.PNG here}
	
   Let's look at this command. John the Ripper needs a wordlist(dictionary) for this attack. "--wordlist=/usr/share/john/password.lst" tells John to use the "password.lst" file located at "/usr/share/john/password.lst". If you want to use a different wordlist, you can change the location and John will take care of the rest. Then, we passed in the file with the hash. John will use the wordlist and the hash and will find the one password that matches the hash.

4. Back in the terminal. Type "john --show hashed_password.txt". This command will show you the word that corresponds to the hash. This is our password.
	{insert Show Password.PNG here} 

