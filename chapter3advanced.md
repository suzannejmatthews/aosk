# How do passwords work?

If you have any online accounts, you are probably familiar with the concept of a password. 
A _password_ is a phrase or sequence of characters that is associated with an account. To 
ensure that the correct person accesses an account online, websites _authenticate_ the person 
logging in by checking first if the inputted username matches a username on record, and if a match 
is found, whether the inputted password matches the password stored along with that username.

In the early days of the internet, username and password information were stored in human-readable 
form called plain-text. These files look like the following:
```
edishungry:password123
aeropixel:racecars
rubycat:scriptkitty
```

In the above file, `edishungry` is an example of a username. This user's asosciated password is 
`password123`. Similarly, `aeropixel`'s password is `racecars`. As you can imagine, storing passwords 
like this is not very secure. Even if a user chooses a strong password, if the company that 
owns the server stores the passwords in plaintext, a hacker that gets ahold of the above file would 
know all the usernames and passwords on the system!

To increase security, most companies _hash_ passwords before they are stored along with usernames. 
A hashed password commonly looks like a long string of random text. So, the corresponding hashed 
password file may look something like:

```
edishungry:482c811da5d5b4bc6d497ffa98491e38
aeropixel:1d615366645ce4a7640755a6f7ad9746
rubycat:13c9a04541cd023982a03b00c8c5e9ea
```

In reality, those long strings are examples of _hashes_. To create a hash, one must use a hash function. 
In the above example, the password hashes are produced by a hash function called MD5. The MD5 hash 
function is _assymetric_ -- that is, it cannot be reversed. If we run the same string 
through MD5 multiple times, we will get the same hash. However, entering two different strings 
(no matter how similar they may be) will _almost always_ result in a different string. We say 
"almost always" because it is possible wtih very low probability. 


## Try it out yourself!
Open the terminal and type the command `echo -n 'scriptkitty' | md5sum`:

```
> echo -n 'scriptkitty' | md5sum
13c9a04541cd023982a03b00c8c5e9ea
```

Run the command multiple times. You will see that you always get the same hash. Now try changing 
`scriptkitty` to `racecars`. Do you get the same hash associated with the username `aeropixel`? 
If you typed it in correctly, you should!

When Ruby types in her username (`rubycat`) into our imaginary website, the server will hash 
her inputted password using MD5, and compare it with the stored hash associated with the 
account `rubycat`. If the hashes match, the website will authenticate Ruby. 

While your password can usually be anything you want, some passwords are better than others. 
As we will see in this tutorial, simple or "weak" passwords are easily guessed. Likewise, 
while using hashes is always better than using plaintext, some hash functions are better than others. 
MD5 (which was widely used in earlier days) is now no longer considered secure. 