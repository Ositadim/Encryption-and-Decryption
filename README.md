Encryption and Decryption

# MODULE 2 — Decrypt an encrypted message (Linux commands)
# Assets, Threats, and Vulnerabilities

# Task 1: Read the contents of a file
# List files in the home directory
ls /home/analyst
# Read the instructions in README.txt
cat README.txt
# Task 2: Find and decrypt a hidden file
# Change to the caesar subdirectory
cd caesar
# List all files, including hidden files
ls -a
# View the contents of the hidden file
cat .leftShift3
# Decrypt the Caesar cipher (left shift by 3)
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"

# Return to the home directory
cd ~
# Task 3: Decrypt the encrypted file
# Decrypt the encrypted file using the revealed OpenSSL command
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
# Confirm the decrypted file exists
ls
# Read the decrypted message
cat Q1.recovered

Activity overview 2
As a security analyst, you’ll need to implement security controls to protect organizations against a range of threats.
That’s where hashing comes in. Previously, you learned that a hash function is an algorithm that produces a code that can’t be decrypted. Hash functions are used to uniquely identify the contents of a file so that you can check whether it has been modified. This code provides a unique identifier known as a hash value or digest.
For example, a malicious program may mimic an original program. If one code line is different from the original program, it produces a different hash value. Security teams can then identify the malicious program and work to mitigate the risk.
Many tools are available to compare hashes for various scenarios. But for a security analyst it’s important to know how to manually compare hashes.
In this lab activity, we’ll create hash values for two files and use Linux commands to manually examine the differences.
Code: 
# MODULE 2 — Create hash values (Linux commands)
# Assets, Threats, and Vulnerabilities
# Task 1: Generate hashes for files

# List the contents of the home directory
ls

# Display the contents of file1.txt
cat file1.txt

# Display the contents of file2.txt
cat file2.txt

# Generate a SHA-256 hash for file1.txt
sha256sum file1.txt

# Generate a SHA-256 hash for file2.txt
sha256sum file2.txt

# Task 2: Compare hashes

# Generate the hash for file1.txt and save it to file1hash
sha256sum file1.txt >> file1hash

# Generate the hash for file2.txt and save it to file2hash
sha256sum file2.txt >> file2hash

# Display the contents of the hash files
cat file1hash
cat file2hash

# Compare the two hash files byte by byte
cmp file1hash file2hash

<img width="940" height="423" alt="image" src="https://github.com/user-attachments/assets/c504d6ea-8741-436e-a8d1-ccfa49a08ec7" />

 

