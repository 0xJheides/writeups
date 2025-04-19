## 🧾 Daily CTF Writeup – [Jangow-01](https://www.vulnhub.com/entry/jangow-101,754/)

**Date:** `[2025-04-19]`  
**Difficulty:** `[Easy]`  
**OS:** `[Linux]`


---



This is the virtualbox that we are going to attack

![jangow 01 vbox](1.png)


**Nmap Results:**  

![nmap result](2.png)

Now the open ports are ftp and apache

![ftp login](3.png)

I tried to login using the anonymous as username and password and we failed to login

![apache](4.png)

I enter the ip address on firefox and a wep app opened i searched everywhere in this website until i found some intersting vulnerabilty


![local file intrusion](5.png)

A local file intrusion(LFI) vulnerabilty

![ls command](6.png)

Played with the parameters by using the unix command line commands such as the ls, now that i found some intersting files, time to read them

![cat](7.png)
![config.php](8.png)

cat command is not working here, so i googled how to cat in a url and i found that you can cat but in base64

![base64](9.png)
```
PD9waHAKJHNlcnZlcm5hbWUgPSAibG9jYWxob3N0IjsKJGRhdGFiYXNlID0gImRlc2FmaW8wMiI7 CiR1c2VybmFtZSA9ICJkZXNhZmlvMDIiOwokcGFzc3dvcmQgPSAiYWJ5Z3VybDY5IjsKLy8gQ3Jl YXRlIGNvbm5lY3Rpb24KJGNvbm4gPSBteXNxbGlfY29ubmVjdCgkc2VydmVybmFtZSwgJHVzZXJu YW1lLCAkcGFzc3dvcmQsICRkYXRhYmFzZSk7Ci8vIENoZWNrIGNvbm5lY3Rpb24KaWYgKCEkY29u bikgewogICAgZGllKCJDb25uZWN0aW9uIGZhaWxlZDogIiAuIG15c3FsaV9jb25uZWN0X2Vycm9y KCkpOwp9CmVjaG8gIkNvbm5lY3RlZCBzdWNjZXNzZnVsbHkiOwpteXNxbGlfY2xvc2UoJGNvbm4p Owo/Pgo= 
```

![using burp](10.png)

Using the burpsuite tool i decoded the base64 and it is a credentials

![attempt to login](11.png)

I used the credentials to login, but i failed to login, time to search some files again 

![another file](12.png)

There's a backup file and it's hidden

![base 64 cat](13.png)

Another base 64 again

![got it](14.png)

Different username, let's try to login

![i'm in](15.png)

I'm in!

![let's find](16.png)

now we are inside, time to get root now that we see the linux version, let's find CVE 

We got the cve 
[CVE:2017-6074](https://www.exploit-db.com/exploits/41458)

Now let's copy the code and write a new file named exploit.c

![exploit](18.png)

Next, we transfer the exploit to the machine by using the PUT

![exploit.c](19.png)

login on the machine using the credentials we got, now that we can see the file we just transfered i compiled the code and run the executable file and now we are now the root user

![login](20.png)

after exploiting, look for the root folder where the flag is

![flag captured](21.png)

# HAPPY HACKING!