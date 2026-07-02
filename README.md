# Encryption, Decryption & File Integrity Verification (Linux)

## Objective

This project focused on applying cryptographic techniques in a Linux environment to protect and verify data — a core responsibility of a security analyst. The first part of the lab involved locating a hidden file, decoding a Caesar cipher to reveal decryption instructions, and using OpenSSL to decrypt an AES-256-CBC encrypted file. The second part involved generating SHA-256 hash values for two files and manually comparing them to detect tampering. Together, these exercises were designed to build practical skills in encryption, secure key derivation, cryptographic hashing, and file integrity verification, foundational controls for protecting organizational assets against threats such as malicious file substitution.

## Skills Learned

* Navigating the Linux command line, including directories, files, and hidden files (`ls -a`, `cd`, `cat`).
* Decrypting AES-256-CBC encrypted files with OpenSSL using secure key derivation (`-pbkdf2`) and Base64-encoded input (`-a`).
* Reversing a Caesar cipher using the `tr` command to remap letters.
* Generating SHA-256 hash values with `sha256sum` to uniquely identify file contents.
* Manually comparing hash outputs byte by byte with `cmp` to detect file modifications.
* Understanding file integrity, tamper detection, and how hash mismatches expose malicious programs mimicking legitimate ones.
* Analyzing authentication and authorization controls and reviewing event logs for suspicious user activity (IAM fundamentals).

## Tools Used

* Google Skills lab platform
* Linux command line (Bash) for file navigation and security-related operations.
* OpenSSL for AES-256-CBC decryption with PBKDF2 key derivation.
* `tr` for character substitution to reverse the Caesar cipher.
* `sha256sum` for cryptographic hash generation.
* `cmp` for byte-by-byte file comparison and integrity verification.

## Steps Taken

## Part 1: Decrypt an Encrypted Message

*Scenario: All files in the home directory have been encrypted following a security incident. The task is to follow the trail, a README, a hidden Caesar-encrypted file, and an OpenSSL command, to recover the original message.*

### Task 1: Read the contents of a file

*Ref 1: Listing the home directory and reading README.txt*

<img width="935" height="88" alt="Listing files and reading README.txt" src="https://github.com/user-attachments/assets/5d2f9c64-6e25-49bd-8d87-e04b8616b2de" />

Listed the files in the home directory with `ls` and read the instructions in `README.txt` using `cat`. The README pointed to a hidden file located in the `caesar` subdirectory.

### Task 2: Find and decrypt a hidden file

*Ref 2: Revealing the hidden file in the caesar subdirectory*

<img width="710" height="121" alt="Listing hidden files and viewing contents" src="https://github.com/user-attachments/assets/7fd98e2e-c509-491a-869b-6229501c96bb" />

Changed into the `caesar` subdirectory and used `ls -a` to list all files, including hidden ones. This revealed `.leftShift3`, whose contents were encrypted with a Caesar cipher.

*Ref 3: Decrypting the Caesar cipher (left shift by 3)*

<img width="532" height="69" alt="Decrypting the Caesar cipher with tr" src="https://github.com/user-attachments/assets/55127681-a150-40a8-9ef4-b52f3f59d47f" />

Used the `tr` command to remap each letter three positions back in the alphabet, reversing the Caesar cipher and revealing the OpenSSL command needed for the next task.

*Ref 4: Returning to the home directory*

<img width="572" height="68" alt="Returning to the home directory" src="https://github.com/user-attachments/assets/1ccfc68b-2e7a-466a-be51-3cae4a6160c7" />

### Task 3: Decrypt the encrypted file

*Ref 5: Running the revealed OpenSSL command*

<img width="788" height="35" alt="OpenSSL decryption command" src="https://github.com/user-attachments/assets/34e8949b-472f-497e-a29a-88536d17a0ae" />

Executed the OpenSSL command revealed in the previous step to decrypt the AES-256-CBC encrypted file.

**Flags explained:**
* `-a` → Base64 encoded input
* `-d` → Decrypt
* `-pbkdf2` → Secure key derivation

*Ref 6: Confirming and reading the decrypted message*

<img width="629" height="93" alt="Reading the decrypted file" src="https://github.com/user-attachments/assets/10c3cb65-162f-47cd-884f-d5afde898cd6" />

Confirmed the decrypted file was created with `ls` and read the recovered plaintext message with `cat`, verifying successful decryption.

## Part 2: Create Hash Values and Verify File Integrity

*Scenario: A malicious program may mimic an original program, if even one line of code differs, it produces a different hash value. As a security analyst, it's important to know how to manually compare hashes to detect tampering. In this activity, hash values are created for two files and Linux commands are used to examine the differences.*

### Task 1: Generate hashes for files

*Ref 7: Displaying file contents and generating SHA-256 hashes*

<img width="558" height="217" alt="Generating SHA-256 hashes for both files" src="https://github.com/user-attachments/assets/a0b0decd-21e3-4f47-8559-5cefef0b510c" />

Listed the home directory contents, displayed `file1.txt` and `file2.txt` with `cat`, both appeared identical on screen, then generated a SHA-256 hash for each with `sha256sum`. The differing hash values immediately indicated the files were not identical despite appearing the same.

### Task 2: Compare hashes

*Ref 8: Saving the hash of file1.txt to file1hash*

<img width="386" height="46" alt="Saving hash of file1.txt" src="https://github.com/user-attachments/assets/87037559-31fe-4807-ae6c-de9913279722" />

*Ref 9: Saving the hash of file2.txt to file2hash*

<img width="409" height="45" alt="Saving hash of file2.txt" src="https://github.com/user-attachments/assets/7bed952f-b555-44b9-84ae-6941f7bcb9ec" />

Redirected each hash output into its own file (`file1hash`, `file2hash`) for manual comparison.

*Ref 10: Displaying the contents of the hash files*

<img width="478" height="101" alt="Hash values side by side" src="https://github.com/user-attachments/assets/95b95077-bc59-4040-a6f7-3546d032690a" />

*Ref 11: Comparing the two hash files byte by byte* <b/>

<img width="275" height="33" alt="cmp comparison of hash files" src="https://github.com/user-attachments/assets/bc46d1c4-09b8-49b9-8e4e-a92b15742891" />

Used `cmp` to compare `file1hash` and `file2hash` byte by byte. Because the files differed, `cmp` reported the exact byte and line where the first mismatch occurred — confirming that `file1.txt` and `file2.txt` do not have identical contents, and demonstrating how hashing exposes even the smallest file modification.

## Key Takeaways

* Hash functions produce a unique digest for file contents, even a one-character change produces a completely different hash, making hashing a reliable tamper-detection control.
* OpenSSL with `-pbkdf2` demonstrates why secure key derivation matters when handling encrypted data.
* Manual hash comparison (`sha256sum` + `cmp`) is a fundamental skill for verifying file integrity without relying on automated tools.

  ## Screenshort
Complete hash comparison workflow <br/>
  <img width="600" height="300" alt="Lab overview" src="https://github.com/user-attachments/assets/84407997-2746-4c37-8de7-4ffe3bbab1b4" />
