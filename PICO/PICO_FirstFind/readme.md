# Writeup: Finding 'uber-secret.txt' in an Archive

## Introduction

This writeup details the process of extracting and locating the file `uber-secret.txt` within a given archive. The goal was to navigate through multiple directories until the hidden file was found.

## Steps to Solve the Challenge

### 1. Extracting the Archive

The first step was to unzip the provided archive. This was done using the following command:

```bash
unzip archive.zip
```

This extracted the contents into a structured directory hierarchy.

### 2. Searching for 'uber-secret.txt'

After extraction, the goal was to locate the file `uber-secret.txt`. Since the structure was not immediately clear, I manually navigated through the directories, checking each folder for the file.

### 3. Locating the File

Through systematic navigation, I found `uber-secret.txt` in the following directory:

```
files\files\adequate_books\more_books\.secret\deeper_secrets\deepest_secrets
```

### 4. Verifying the File

Once found, I opened the file using:

```bash
cat files/files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```

This confirmed that the file contained the expected secret information.

## Conclusion

The challenge involved extracting an archive and methodically searching through nested directories to locate a hidden file. The solution was achieved through careful directory traversal and verification of contents.
