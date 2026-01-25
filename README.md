Below is a clean **HTML README** you can paste into a file named `README.html` in your GitHub repo. It’s based on the steps and lab content in your PDF (encryption/decryption + hashing tasks + access control worksheet activity). 

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Encryption & Decryption (Linux) — Lab Notes</title>
  <style>
    body { font-family: Arial, Helvetica, sans-serif; line-height: 1.55; margin: 0; background:#0b0f14; color:#e8eef6;}
    main { max-width: 980px; margin: 0 auto; padding: 32px 18px; }
    h1,h2,h3 { line-height: 1.2; }
    .card { background:#111824; border:1px solid #223046; border-radius:14px; padding:18px; margin:16px 0; }
    code, pre { font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace; }
    pre { background:#0a1220; border:1px solid #223046; border-radius:12px; padding:14px; overflow:auto; }
    .tag { display:inline-block; padding:4px 10px; border-radius:999px; background:#1a2840; border:1px solid #2b4268; margin-right:8px; font-size:12px; }
    a { color:#8ab4ff; }
    ul { margin-top: 8px; }
    .muted { color:#b7c3d6; }
    .grid { display:grid; gap:14px; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); }
  </style>
</head>
<body>
  <main>
    <header>
      <h1>Encryption & Decryption (Linux) — Lab Notes</h1>
      <p class="muted">
        This repository documents Linux command-line exercises covering:
        decrypting Caesar ciphers, decrypting AES-encrypted files with OpenSSL, generating SHA-256 hashes,
        and a short access-control analysis activity.
      </p>
      <p>
        <span class="tag">Cybersecurity</span>
        <span class="tag">Linux CLI</span>
        <span class="tag">Encryption</span>
        <span class="tag">Hashing</span>
        <span class="tag">Access Controls</span>
      </p>
    </header>

    <section class="card">
      <h2>What You’ll Learn</h2>
      <ul>
        <li>How to read files and navigate directories using Linux commands.</li>
        <li>How to decrypt a simple Caesar cipher using <code>tr</code>.</li>
        <li>How to decrypt an AES-256-CBC encrypted file using <code>openssl</code>.</li>
        <li>How to generate and compare SHA-256 hash values using <code>sha256sum</code> and <code>cmp</code>.</li>
        <li>How to assess access-control weaknesses and recommend mitigations.</li>
      </ul>
    </section>

    <section class="card">
      <h2>Module 2 — Decrypt an Encrypted Message (Linux Commands)</h2>

      <h3>Task 1: Read the contents of a file</h3>
      <pre><code>ls /home/analyst
cat README.txt</code></pre>

      <h3>Task 2: Find and decrypt a hidden file (Caesar cipher)</h3>
      <pre><code>cd caesar
ls -a
cat .leftShift3

# Decrypt Caesar cipher (left shift by 3)
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"

cd ~</code></pre>
      <p class="muted">
        The <code>tr</code> mapping shifts letters back by 3 to recover the plaintext.
      </p>

      <h3>Task 3: Decrypt the encrypted file (OpenSSL AES-256-CBC)</h3>
      <pre><code>openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute

ls
cat Q1.recovered</code></pre>
      <p class="muted">
        Notes: <code>-a</code> indicates base64 input, <code>-d</code> decrypts, and <code>-pbkdf2</code> uses PBKDF2 for key derivation.
      </p>
    </section>

    <section class="card">
      <h2>Module 2 — Create Hash Values (Linux Commands)</h2>
      <p class="muted">
        Hashing helps detect file changes: even a one-line difference creates a different digest.
      </p>

      <h3>Task 1: Generate hashes for files</h3>
      <pre><code>ls
cat file1.txt
cat file2.txt

sha256sum file1.txt
sha256sum file2.txt</code></pre>

      <h3>Task 2: Compare hashes</h3>
      <pre><code>sha256sum file1.txt &gt;&gt; file1hash
sha256sum file2.txt &gt;&gt; file2hash

cat file1hash
cat file2hash

# Compare the two hash files byte by byte
cmp file1hash file2hash</code></pre>
      <p class="muted">
        If the files differ, <code>cmp</code> reports the first byte position/line where they diverge.
      </p>
    </section>

    <section class="card">
      <h2>Access Controls Worksheet — Mini Investigation</h2>
      <p class="muted">
        Scenario summary: a business stopped a suspicious deposit to an unknown bank account. Your job is to
        review logs, identify access-control issues, and recommend mitigations.
      </p>

      <div class="grid">
        <div class="card" style="margin:0;">
          <h3>What to Examine</h3>
          <ul>
            <li>Event log details (event type, date/time, IP address)</li>
            <li>Employee directory information</li>
            <li>Overlap between the two (to identify likely misuse)</li>
          </ul>
        </div>

        <div class="card" style="margin:0;">
          <h3>What to Produce</h3>
          <ul>
            <li>1–2 notes about the user from the event log</li>
            <li>1–2 access-control issues discovered</li>
            <li>At least 2 mitigation recommendations</li>
          </ul>
        </div>
      </div>

      <h3>Example Issues & Mitigations (Template)</h3>
      <ul>
        <li><strong>Issue:</strong> Access not revoked when employees leave (or role changes).</li>
        <li><strong>Mitigation:</strong> Add an offboarding checklist that immediately disables accounts and removes shared-drive access.</li>
        <li><strong>Issue:</strong> Overly broad permissions in a shared cloud drive.</li>
        <li><strong>Mitigation:</strong> Enforce least privilege with role-based access control (RBAC) and periodic access reviews.</li>
      </ul>
    </section>

    <section class="card">
      <h2>How to Run (Quick Start)</h2>
      <ol>
        <li>Open a Linux terminal.</li>
        <li>Copy/paste each command block in order.</li>
        <li>Confirm outputs with <code>ls</code> and read recovered files with <code>cat</code>.</li>
      </ol>
    </section>

    <section class="card">
      <h2>Folder Structure (Suggested)</h2>
      <pre><code>.
├─ README.html
├─ notes/
│  ├─ decryption-notes.md
│  └─ hashing-notes.md
└─ screenshots/
   └─ (optional images of terminal output)</code></pre>
    </section>

    <footer class="muted" style="margin-top:22px;">
      <p>
        Source material: "Encryption and Decryption" lab handout. (See attached PDF in this repo or project folder.)
      </p>
    </footer>
  </main>
</body>
</html>
```
