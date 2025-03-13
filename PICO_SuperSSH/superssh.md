# Challenge Name: Super SSH

## Challenge Overview

This challenge required using Secure Shell (SSH) to connect to a remote server and retrieve a flag. SSH is a widely used protocol for securely accessing remote systems, making it an essential skill in cybersecurity.

## Steps to Solve

1. **Connecting via SSH**

   - The challenge provided an SSH port and credentials to connect to the remote server.
   - The command used to initiate the SSH connection was:

     ```bash
     ssh -p {port} {player}@titan.picoctf.net
     ```

2. **Handling the Host Key Verification**

   - Upon connecting, a message indicated that the authenticity of the host could not be established.
   - To proceed, I entered `yes` to add the server to the list of known hosts.

3. **Entering the Password**

   - The system prompted for a password, which was provided as part of the challenge details.

4. **Retrieving the Flag**
   - After a successful login, the server displayed a welcome message along with the flag:

     ```
     picoCTF{s3cur3_c0nn3ct10n_3e293eea}
     ```

   - The connection was then automatically closed.

## Conclusion

This challenge demonstrated the fundamental use of SSH for remote access. Successfully connecting to the server and retrieving the flag required understanding SSH commands, handling host verification, and entering credentials correctly.

## Key Takeaways

- SSH is an essential tool for secure remote access.
- Always verify the authenticity of a host before connecting.
- Using different ports for SSH connections can enhance security.
- Flags in CTF challenges are often displayed upon successful authentication.
