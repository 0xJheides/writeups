# PicoCTF 2024 - QR Code Flag Extraction Writeup

## Challenge Overview

This challenge provided a `challenge.zip` file containing an image instead of a traditional text-based flag. The goal was to extract the flag by scanning the QR code within the image.

## Steps to Solve

### Step 1: Download and Extract the ZIP File

The first step was to download and extract the contents of the ZIP archive:

```
unzip challenge.zip
```

This revealed an image file.

### Step 2: Scan the QR Code

Since the flag was embedded as a QR code, I needed to decode it. I used an online QR code scanner by uploading the image to:

```
https://scanqr.org/
```

### Step 3: Retrieve the Flag

The QR scanner successfully decoded the flag from the image, completing the challenge.

## Conclusion

By simply extracting the ZIP file and scanning the QR code, I was able to retrieve the flag without any need for decryption scripts or hash verification.

---

### Key Takeaways

- Extracted a **ZIP file** to access the challenge contents.
- Used an **online QR scanner** to decode the flag.
- No need for **checksum verification** or **decryption scripts** in this challenge variation.
