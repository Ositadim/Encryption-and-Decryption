Perfect — I’ll **organise exactly what’s in your file into a clean, professional GitHub README**, **without adding new content**, and **with placeholders that retain your screenshots** (so GitHub renders them).
You can copy-paste this directly into `README.md`.

Everything below is structured **only from your uploaded file**. 

---

# 🔐 Encryption and Decryption (Linux)

This repository documents hands-on **Linux command-line exercises** focused on **encryption, decryption, hashing, and access control analysis**.
The project demonstrates practical cybersecurity skills used by entry-level security analysts.

---

## 📂 Project Overview

This lab covers three core security tasks:

* Decrypting encrypted messages using Linux commands
* Creating and comparing hash values to detect file tampering
* Assessing access-control weaknesses and proposing mitigations

---

## 🧩 Module 2 — Decrypt an Encrypted Message (Linux Commands)

### 🎯 Objective

Learn how encrypted messages can be decrypted using Linux utilities such as `tr` and `openssl`.

---

### 🔹 Task 1: Read the contents of a file

List files in the home directory and read the provided instructions.

```bash
ls /home/analyst
cat README.txt
```

📸 **Screenshot:**
*(Insert screenshot showing directory listing and README contents)*

```md
![Reading README file](screenshots/readme-file.png)
```

---

### 🔹 Task 2: Find and decrypt a hidden file (Caesar cipher)

Navigate to the Caesar cipher directory and reveal hidden files.

```bash
cd caesar
ls -a
cat .leftShift3
```

Decrypt the hidden file using a left shift of 3:

```bash
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
```

Return to the home directory:

```bash
cd ~
```

📸 **Screenshot:**
*(Insert screenshot showing hidden file and decrypted output)*

```md
![Caesar cipher decryption](screenshots/caesar-decryption.png)
```

---

### 🔹 Task 3: Decrypt an encrypted file using OpenSSL

Decrypt the AES-256-CBC encrypted file using the provided key.

```bash
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```

Confirm the file and read the decrypted message:

```bash
ls
cat Q1.recovered
```

📸 **Screenshot:**
*(Insert screenshot showing successful decryption output)*

```md
![OpenSSL decryption](screenshots/openssl-decryption.png)
```

---

## 🔑 Module 2 — Create Hash Values (Linux Commands)

### 🎯 Objective

Understand how hashing is used to verify file integrity and detect tampering.

---

### 🔹 Task 1: Generate SHA-256 hash values

Display file contents and generate hashes.

```bash
ls
cat file1.txt
cat file2.txt

sha256sum file1.txt
sha256sum file2.txt
```

📸 **Screenshot:**
*(Insert screenshot showing hash generation)*

```md
![SHA-256 hashes](screenshots/hash-generation.png)
```

---

### 🔹 Task 2: Compare hash values

Save the hashes into files:

```bash
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash
```

View the hash files:

```bash
cat file1hash
cat file2hash
```

Compare them byte by byte:

```bash
cmp file1hash file2hash
```

📸 **Screenshot:**
*(Insert screenshot showing hash comparison output)*

```md
![Hash comparison](screenshots/hash-comparison.png)
```

---

## 🛂 Access Controls Worksheet — Security Analysis

### 🎯 Objective

Analyze an access-control failure that nearly resulted in financial loss and recommend security improvements.

---

### 📖 Scenario Summary

A growing business almost transferred money to an unknown bank account.
The transaction was stopped, and the owner requested an investigation to prevent future incidents.

---

### 🔍 Investigation Steps

* Reviewed **event logs** (event type, date, time, IP address)
* Compared logs with the **employee directory**
* Identified access-control weaknesses
* Proposed security mitigations

📸 **Screenshot:**
*(Insert screenshot of event log and worksheet)*

```md
![Access control worksheet](screenshots/access-control.png)
```

---

### ⚠️ Identified Issues (Examples)

* Access was not revoked after employee role changes
* Shared cloud drive permissions were overly broad

---

### ✅ Recommended Mitigations

* Revoke system access immediately during employee offboarding
* Apply least-privilege access control
* Conduct regular access audits
* Restrict shared resource permissions

---

## 🗂️ Suggested Repository Structure

```
.
├── README.md
├── screenshots/
│   ├── readme-file.png
│   ├── caesar-decryption.png
│   ├── openssl-decryption.png
│   ├── hash-generation.png
│   ├── hash-comparison.png
│   └── access-control.png
```

---

## 📚 Source

This project is based on the **Encryption and Decryption** lab covering Linux-based cryptography, hashing, and access-control analysis. 

---

If you want, next I can:

* Rename screenshots for you exactly as GitHub expects
* Tighten the language for **recruiters / portfolios**
* Add a **skills section** (Linux, OpenSSL, Hashing, IAM)
* Convert this into **Google Cybersecurity Certificate–style documentation**

Just tell me 👍
