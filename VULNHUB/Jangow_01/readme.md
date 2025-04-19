# 🧾 Daily CTF Writeup – [Jangow-01](https://www.vulnhub.com/entry/jangow-101,754/)

**Date:** `2025-04-19`  
**Difficulty:** `Easy`    
**OS:** `Linux`   
**Hecker:** `Jerome Infante`


---

## 💻 Target Setup

This is the VirtualBox machine we’re targeting:

![jangow 01 vbox](1.png)

---

## 🔎 Reconnaissance

**Nmap Scan Results:**

![nmap result](2.png)

The scan shows that FTP and Apache are running.

---

## 📂 FTP Enumeration

![ftp login](3.png)

Tried logging into FTP using `anonymous` credentials — access was denied.

---

## 🌐 Web Enumeration

Navigated to the target IP in Firefox. A web application loaded.

![apache](4.png)

After browsing through the site, I discovered a vulnerability.

---

## 🛠️ Exploitation – LFI Discovery

![local file intrusion](5.png)

Found a **Local File Inclusion (LFI)** vulnerability.

Started playing around with parameters using Linux commands like `ls`.

![ls command](6.png)

Located some interesting files. Time to read them.

---

## 📜 Reading Sensitive Files (Base64 Trick)

Tried using the `cat` command via URL but it didn’t work directly.

![cat](7.png)  
![config.php](8.png)

Googled for workarounds and found you can output files using `base64` encoding.

![base64](9.png)

Decoded the base64 using **Burp Suite**:

![using burp](10.png)

**Credentials recovered:**

***Username***: desafio02

***Password***: abygurl69


---

## 🔐 Login Attempt (Failed)

![attempt to login](11.png)

Tried logging in with the credentials — failed.

Back to searching for more files…

---

## 📁 Hidden Backup File Found

![another file](12.png)

Discovered a hidden backup file — also in base64.

![base 64 cat](13.png)

Decoded it and got another set of credentials.

![got it](14.png)

---

## ✅ Successful Login

![i'm in](15.png)

Used the new credentials and successfully logged in.

---

## 📈 Privilege Escalation

Now that we’re in, the next step is rooting the box.

![let's find](16.png)

Checked the Linux version and looked for a suitable CVE.

Found one: [CVE-2017-6074](https://www.exploit-db.com/exploits/41458)

---

## 🧨 Local Exploit

Copied the exploit code into a new file: `exploit.c`

![exploit](18.png)

Uploaded it to the target using **PUT**.

![exploit.c](19.png)

Logged into the machine, compiled the exploit, and executed it.

Boom — **root access** achieved.

---

## 🏁 Capture the Flag

![login](20.png)

Navigated to the `/root` directory.

![flag captured](21.png)

**Flag captured! Mission complete.**

---

## 🎉 Final Notes

- Solid practice on LFI exploitation and base64 tricks.  
- Always check for hidden/backup files.  
- CVE-based privilege escalation was smooth with the right kernel version.

---

# 🔚 HAPPY HACKING!
