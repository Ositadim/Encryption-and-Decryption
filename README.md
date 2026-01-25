**Encryption and Decryption**

Skills Demonstrated
- Linux (Command Line)
- Navigating directories and files (ls, cd, cat)
- Working with hidden files

Executing security-related commands in a Linux environment
🔐 OpenSSL
- Decrypting AES-256-CBC encrypted files
- Using secure key derivation (-pbkdf2)
- Handling Base64-encoded encrypted data
- Verifying successful decryption through file inspection

Cryptographic Hashing
- Generating SHA-256 hash values with sha256sum
- Understanding file integrity and tamper detection
- Comparing hash outputs manually using cmp
- Identifying file changes through hash mismatches

Identity & Access Management (IAM)
- Analyzing authentication and authorization controls
- Reviewing event logs to identify suspicious user activity

MODULE 2 — Decrypt an encrypted message (Linux commands)
##Assets, Threats, and Vulnerabilities
Task 1: Read the contents of a file
- List files in the home directory and Read the instructions in README.txt
  <img width="935" height="88" alt="image" src="https://github.com/user-attachments/assets/5d2f9c64-6e25-49bd-8d87-e04b8616b2de" />

Task 2: Find and decrypt a hidden file
Change to the caesar subdirectory, list all files, including hidden files and to view the contents of the hidden file.

<img width="710" height="121" alt="image" src="https://github.com/user-attachments/assets/7fd98e2e-c509-491a-869b-6229501c96bb" />

Decrypt the Caesar cipher (left shift by 3)

<img width="532" height="69" alt="image" src="https://github.com/user-attachments/assets/55127681-a150-40a8-9ef4-b52f3f59d47f" />

Return to the home directory 

<img width="572" height="68" alt="image" src="https://github.com/user-attachments/assets/1ccfc68b-2e7a-466a-be51-3cae4a6160c7" />

## The tr command remaps letters to reverse the Caesar cipher.

Task 3: Decrypt the encrypted file
Decrypt the encrypted file using the revealed OpenSSL command
<img width="788" height="35" alt="image" src="https://github.com/user-attachments/assets/34e8949b-472f-497e-a29a-88536d17a0ae" />

Confirm the decrypted file exists and Read the decrypted message

<img width="629" height="93" alt="image" src="https://github.com/user-attachments/assets/10c3cb65-162f-47cd-884f-d5afde898cd6" />

**Note**: Flags explained
-a → Base64 encoded input
-d → Decrypt
-pbkdf2 → Secure key derivation

**Activity overview 2**
As a security analyst, you’ll need to implement security controls to protect organizations against a range of threats.
That’s where hashing comes in. Previously, you learned that a hash function is an algorithm that produces a code that can’t be decrypted. Hash functions are used to uniquely identify the contents of a file so that you can check whether it has been modified. This code provides a unique identifier known as a hash value or digest.
For example, a malicious program may mimic an original program. If one code line is different from the original program, it produces a different hash value. Security teams can then identify the malicious program and work to mitigate the risk.
Many tools are available to compare hashes for various scenarios. But for a security analyst it’s important to know how to manually compare hashes.
In this lab activity, we’ll create hash values for two files and use Linux commands to manually examine the differences.
Code: 
MODULE 2 — Create hash values (Linux commands)

Task 1: Generate hashes for files
List the contents of the home directory
- ls

Display the contents of file1.txt
- cat file1.txt
Display the contents of file2.txt
- cat file2.txt

Generate a SHA-256 hash for file1.txt
- sha256sum file1.txt

Generate a SHA-256 hash for file2.txt
- sha256sum file2.txt
  
<img width="558" height="217" alt="image" src="https://github.com/user-attachments/assets/a0b0decd-21e3-4f47-8559-5cefef0b510c" />

Task 2: Compare hashes
Generate the hash for file1.txt and save it to file1hash
- sha256sum file1.txt >> file1hash

Generate the hash for file2.txt and save it to file2hash
- sha256sum file2.txt >> file2hash
  
<img width="577" height="88" alt="image" src="https://github.com/user-attachments/assets/c3f12eed-69aa-4506-8f8d-865f8ebc2eee" />

Display the contents of the hash files
- cat file1hash
- cat file2hash
  
<img width="478" height="101" alt="image" src="https://github.com/user-attachments/assets/95b95077-bc59-4040-a6f7-3546d032690a" />

. Compare the two hash files byte by byte
cmp file1hash file2hash
- If the files differ, cmp reports the exact location of the mismatch.

<img width="600" height="523" alt="image" src="https://github.com/user-attachments/assets/84407997-2746-4c37-8de7-4ffe3bbab1b4" />

Manual Practice on the use of cryptography, encryption and #Hashing in protecting data or information.
 
<img width="527" height="174" alt="image" src="https://github.com/user-attachments/assets/fff8f55f-47e0-41ce-8969-3cb842f384dc" /><br/>


<img width="455" height="302" alt="image" src="https://github.com/user-attachments/assets/23c3f217-768e-43ae-98f8-794adfcee63e" /><br/>


<img width="534" height="151" alt="image" src="https://github.com/user-attachments/assets/9f18a1eb-1f81-4c5e-b9f3-bee5750f63b8" />

