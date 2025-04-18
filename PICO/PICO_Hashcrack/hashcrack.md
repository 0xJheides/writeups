# Weak Hashing Exploitation - picoCTF Challenge

## Challenge Description
A company stored a secret message on a server, but due to the administrator using weakly hashed passwords, the server was breached. Can you gain access to the secret stored within the server?

Access the server using:
```sh
nc verbal-sleep.picoctf.net 52518
```

## Solution
To solve this challenge, I leveraged **CrackStation**, an online hash-cracking tool, to reveal the plaintext values of the given hashes.

### Step 1: Cracking the First Hash (MD5)
```
Identified hash: 482c811da5d5b4bc6d497ffa98491e38
```
Using CrackStation, the plaintext password for this MD5 hash is:
```
password123
```
Entering this password returned:
```
Correct! You've cracked the MD5 hash with no secret found!
```

### Step 2: Cracking the Second Hash (SHA-1)
```
Identified hash: b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3
```
Using CrackStation, the plaintext password for this SHA-1 hash is:
```
letmein
```
Entering this password returned:
```
Correct! You've cracked the SHA-1 hash with no secret found!
```

### Step 3: Cracking the Final Hash (SHA-256)
```
Identified hash: 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745
```
Using CrackStation, the plaintext password for this SHA-256 hash is:
```
qwerty098
```
Entering this password revealed the flag:
```
Correct! You've cracked the SHA-256 hash with a secret found.
The flag is: picoCTF{UseStr0nG_h@shEs_&PaSswDs!_70ffa57c}
```

## Conclusion
This challenge highlights the importance of using strong passwords and secure hashing algorithms. **MD5, SHA-1, and even SHA-256 can be cracked if weak passwords are used.** Always use salted and computationally expensive hashing methods (e.g., bcrypt, Argon2) for password storage.

### Flag
```
picoCTF{UseStr0nG_h@shEs_&PaSswDs!_70ffa57c}
```

