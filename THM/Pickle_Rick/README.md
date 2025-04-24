# 🧾 Daily CTF Writeup – [Pickle Rick](https://tryhackme.com/room/picklerick)

- **Date:** 2025-04-24  
- **Difficulty:** Easy  
- **OS:** Linux  
- **Hecker:** Jerome Infante  

---

## 🔎 Reconnaissance

### 🔍 Nmap Scan Results

![nmap result](1.png)  
The scan reveals that **SSH** and **Apache** are running on the target machine.

---

## 🌐 Web Application

![ftp login](2.png)  
A basic **web app** is hosted and accessible via the browser.

---

## 🔍 Web Enumeration

![apache](3.png)  
By inspecting the page source, I discovered an **account username** hardcoded in the HTML.

---

## 🛠️ Directory Busting

![local file intrusion](4.png)  
I performed dirbusting to search for hidden files and directories.

![ls command](5.png)  
Found a **login page** and a `robots.txt` file. The file revealed a **password**, which matches the previously found username.

---

## 📜 Command Injection to Read Files

After logging in, I found a field vulnerable to **command injection**.

![cat](6.png)  
Using commands like `ls`, I discovered new `.txt` files containing clues.

![using burp](7.png)  
Attempted to use the web form to read them with `cat`, but it didn’t work properly in the response.

![using burp](8.png)  
A clue mentioned that the **flags are hidden deeper in the system**.

---

## 📁 Hidden Backup File Found

![another file](9.png)  
Discovered a hidden backup file and retrieved the **first flag**



---

## 🖥️ Reverse Shell Access
Used the vulnerability to spawn a **reverse shell**, gaining full access to the system.

![base 64 cat](10.png)  
![got it](11.png)  
![got it](12.png)  

---

# 🔚 HAPPY HACKING!
