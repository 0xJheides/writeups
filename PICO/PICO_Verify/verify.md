# PicoCTF 2024 - Flag Verification Writeup

## Challenge Overview

The challenge provided a remote SSH connection to a server where imitation flags were being used to trick players. The goal was to verify the legitimacy of the correct flag using a given SHA-256 checksum and decrypt the correct file.

## Given Information

- **SSH Connection:** `ssh -p {depends on your account} ctf-player@{depends on your account}.picoctf.net`
- **Password:** `{depends on your account}`
- **Checksum:** `fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7`
- **Decryption Script:** `./decrypt.sh files/<file>`

## Steps to Solve

### Step 1: Connect to the Remote Server

First, I connected to the given server using SSH:

```
ssh -p 1234 ctf-player@test.picoctf.net
```

After entering the given password (`test`), I accepted the fingerprint by typing `yes` when prompted.

### Step 2: List Files and Verify Checksum

Once inside the server, I listed the files to see the contents:

```
ls
```

This revealed a `checksum.txt` file, which I displayed using:

```
cat checksum.txt
```

Next, I navigated to the `files/` directory to inspect available files:

```
cd files
ls
```

To identify the correct file, I computed the SHA-256 hash of all files and matched it with the provided checksum:

```
sha256sum * | grep fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7
```

This returned the correct file, `87590c24`.

### Step 3: Decrypt the Flag

After identifying the correct file, I navigated back to the main directory:

```
cd ../
```

Then, I ran the decryption script on the verified file:

```
./decrypt.sh ./files/87590c24
```

This revealed the final flag.

## Conclusion

By verifying the file’s checksum before decrypting, I ensured I retrieved the legitimate flag. This method prevented me from falling for any fake flags placed in the directory.

---

### Key Takeaways

- Used **SSH** to access the remote server.
- Verified file integrity using **SHA-256 checksum**.
- Used the **decryption script** to retrieve the legitimate flag.
- Avoided fake flags by following a structured verification process.
