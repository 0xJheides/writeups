# README: Running the runme.py Script to Get the Flag

## Introduction

This document details the process of obtaining a flag by downloading and executing a Python script named `runme.py`. The script was retrieved using `wget` and executed using Python.

## Steps to Obtain the Flag

### 1. Downloading the Script

The first step was to download the script using `wget` in a webshell. The command used was:

```bash
wget <URL-to-runme.py>
```

This command fetches the `runme.py` script from the given URL and saves it to the current directory.

### 2. Verifying the Download

After downloading, it is good practice to check if the file exists and view its contents to ensure it is safe to run:

```bash
ls -l runme.py  # Check if the file is present
cat runme.py    # Inspect the script's contents
```

### 3. Executing the Script

Once verified, the script was executed using Python3:

```bash
python3 runme.py
```

### 4. Obtaining the Flag

After executing the script, it printed out a flag, which was the expected output. The flag was successfully retrieved and recorded.

## Conclusion

This task involved a straightforward process of downloading and running a Python script to obtain a flag. The key steps included using `wget` for retrieval, verifying the script, and executing it with Python3. Always remember to inspect scripts before running them to avoid potential security risks.
