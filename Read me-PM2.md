<div align="center">

# 🔐 Password Cracking with Networkwalks Tools

**W3-PM2 | Week 3 | Project Module 2**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Tool-NW%20Hash%20Calculator-E87500?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Tool-NW%20Password%20Cracker-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Platform-Windows%20%2F%20Browser-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Networkwalks-B082-404040?style=flat-square&labelColor=C00000" />
</p>

---

## 📌 Project Overview

This module covers **browser-based password cracking using two free tools built by Networkwalks** — the Hash Calculator and the Password Cracker. Unlike JTR which runs as a local application, both tools run entirely inside a web browser with no installation required, making them accessible on any device including Windows, Mac, Kali Linux, or a phone.

The workflow mirrors the exact same concept used by JTR:
1. Extract the password hash from the protected file.
2. Run a dictionary attack — hash every word in a wordlist and compare it to the extracted hash.
3. When a match is found, the original password is recovered.

Two locked PDF files were cracked in this module, demonstrating how the same tool handles files with different password complexities.

---

## 🎯 Objective

Crack the passwords of two locked PDF files using the Networkwalks Hash Calculator and Password Cracker tools in a web browser.

---

## 🏗️ Lab Environment

| Component | Configuration |
|---|---|
| 🖥️ OS | Windows 10 (Host PC) |
| 🌐 Tool 1 | Networkwalks Hash Calculator — https://networkwalks.com/hash-calculator/ |
| 🌐 Tool 2 | Networkwalks Password Cracker — https://networkwalks.com/password-cracker/ |
| 🎯 Target File 1 | My Locked PDF1.pdf |
| 🔑 Password 1 | **password1** |
| 🎯 Target File 2 | My Locked PDF2.pdf |
| 🔑 Password 2 | **1qaz2wsx** |

> **Note:** Both tools process files and compute hashes entirely in your browser. No text or file is ever uploaded to a server. All hashing happens locally using the Web Crypto API.

---

## 🪜 Task Execution

---

## 🔒 PDF 1 — My Locked PDF1.pdf → password1

---

### Step 1 — Download the Encrypted PDF

Downloaded the locked PDF file from the Networkwalks lab page:

[https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/](https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/)

> 📸 **Screenshot:** `screenshots/pdf1-step1-download-page.png`
>
> *(Insert screenshot of the Networkwalks lab page showing the download link for My Locked PDF1.pdf)*

---

### Step 2 — Open the Networkwalks Hash Calculator

Opened the Hash Calculator in a web browser:

[https://networkwalks.com/hash-calculator/](https://networkwalks.com/hash-calculator/)

The tool has three tabs: **Text**, **File**, and **PDF**. Selected the **PDF** tab.

> 📸 **Screenshot:** `screenshots/pdf1-step2-hash-calculator-open.png`
>
> *(Insert screenshot of the Networkwalks Hash Calculator page in the browser, with the PDF tab selected)*

---

### Step 3 — Upload the Locked PDF & Extract Hash

In the PDF tab, clicked the upload area and selected `My Locked PDF1.pdf`. The tool read the file locally and extracted a crackable hash value.

The hash was displayed in the **PDF Hash** field, starting with `$pdf$4*4*128*...`

> 📸 **Screenshot:** `screenshots/pdf1-step3-hash-extracted.png`
>
> *(Insert screenshot of the Hash Calculator showing the extracted $pdf$ hash for My Locked PDF1.pdf, with the Copy button visible)*

---

### Step 4 — Copy the Full Hash Value

Clicked the **Copy** button to copy the complete hash string.

**Important:** The hash must include everything starting from `$pdf$`. Do not miss any characters from the beginning or end of the string.

The extracted hash for this PDF:
```
$pdf$4*4*128*-1060*1*16*55d1a5c14175da44975399e44971d32*32*777fd021a7f3c5ae598c8c6d9bc7f76e00000000000000000000000000000000*32*ceecdac74b19b5a6268bd3b3524e1374c955cbb9cc3c45316494d9446ef81af1
```

> 📸 **Screenshot:** `screenshots/pdf1-step4-hash-copied.png`
>
> *(Insert screenshot showing the hash selected or the Copy button being clicked, confirming the full $pdf$ hash is captured)*

---

### Step 5 — Open the Networkwalks Password Cracker

Opened the Password Cracker tool in a new browser tab:

[https://networkwalks.com/password-cracker/](https://networkwalks.com/password-cracker/)

The tool is a **Dictionary Attack Lab** — it hashes every word in a wordlist and matches it against the PDF hash, using the same core idea as John the Ripper.

> 📸 **Screenshot:** `screenshots/pdf1-step5-password-cracker-open.png`
>
> *(Insert screenshot of the Networkwalks Password Cracker tool in the browser, showing the empty PDF HASH field and the START CRACKING button)*

---

### Step 6 — Paste Hash & Start Cracking

Pasted the copied hash into the **PDF HASH ($PDF$...)** text area. Left the wordlist on the default **Built-in list (100 passwords)** setting. Clicked **START CRACKING**.

The tool began working through its wordlist, hashing each word and comparing it to the PDF hash. A live log showed each attempt in real time:

```
[-] Trying: service ✗
[-] Trying: canada ✗
[-] Trying: hockey ✗
[-] Trying: killer ✗
[-] Trying: george ✗
[-] Trying: asdqeh ✗
[-] Trying: zxcvbn ✗
[-] Trying: qwertyuiop ✗
[-] Trying: 111223 ✗
[+] MATCH password1 ✓
```

> 📸 **Screenshot:** `screenshots/pdf1-step6-hash-pasted-cracking.png`
>
> *(Insert screenshot of the Password Cracker with the hash pasted in the field and the attack running, showing the live log of attempted passwords)*

---

### Step 7 — Password Cracked

The tool found the matching password and displayed the result.

**PASSWORD CRACKED SUCCESSFULLY**

**🔑 Password: `password1`**

> 📸 **Screenshot:** `screenshots/pdf1-step7-password-cracked.png`
>
> *(Insert screenshot of the Password Cracker showing "PASSWORD CRACKED SUCCESSFULLY" and the password "password1" in green text, with the Copy password button)*

---

### Step 8 — Open the Locked PDF

Opened `My Locked PDF1.pdf` in Adobe Acrobat Reader. When prompted for a password, entered `password1`.

The PDF unlocked successfully.

> 📸 **Screenshot:** `screenshots/pdf1-step8-pdf-password-prompt.png`
>
> *(Insert screenshot of Adobe Acrobat showing the "Enter Password" dialog for My Locked PDF1.pdf)*

> 📸 **Screenshot:** `screenshots/pdf1-step8-pdf-unlocked.png`
>
> *(Insert screenshot of the PDF open and unlocked, showing the content inside — the Congratulations / flag page)*

---

## 🔒 PDF 2 — My Locked PDF2.pdf → 1qaz2wsx

---

### Step 1 — Open the Hash Calculator & Upload PDF 2

Returned to the Networkwalks Hash Calculator and uploaded the second locked PDF file, `My Locked PDF2.pdf`.

The tool extracted a new hash value for this file.

> 📸 **Screenshot:** `screenshots/pdf2-step1-hash-extracted.png`
>
> *(Insert screenshot of the Hash Calculator showing the extracted hash for My Locked PDF2.pdf)*

---

### Step 2 — Copy Hash & Open Password Cracker

Copied the full hash value for PDF 2 and opened the Password Cracker. Pasted the hash into the PDF HASH field.

> 📸 **Screenshot:** `screenshots/pdf2-step2-hash-pasted.png`
>
> *(Insert screenshot of the Password Cracker with PDF 2's hash pasted in the hash field)*

---

### Step 3 — Start Cracking

Clicked **START CRACKING**. The built-in wordlist was used. The tool tried passwords sequentially until it reached `1qaz2wsx` — a common keyboard-pattern password.

> 📸 **Screenshot:** `screenshots/pdf2-step3-cracking-in-progress.png`
>
> *(Insert screenshot of the Password Cracker mid-attack for PDF 2, showing the live log of attempted passwords)*

---

### Step 4 — Password Cracked

**PASSWORD CRACKED SUCCESSFULLY**

**🔑 Password: `1qaz2wsx`**

> 📸 **Screenshot:** `screenshots/pdf2-step4-password-cracked.png`
>
> *(Insert screenshot showing "PASSWORD CRACKED SUCCESSFULLY" with "1qaz2wsx" displayed in the result box)*

---

### Step 5 — Open the Second Locked PDF

Opened `My Locked PDF2.pdf` and entered the cracked password `1qaz2wsx`. The PDF unlocked successfully.

> 📸 **Screenshot:** `screenshots/pdf2-step5-pdf-unlocked.png`
>
> *(Insert screenshot of PDF 2 open and unlocked, showing the content inside)*

---

## 📊 Summary of Results

| Item | PDF 1 | PDF 2 |
|---|---|---|
| File | My Locked PDF1.pdf | My Locked PDF2.pdf |
| Hash Prefix | $pdf$4*4*128*... | $pdf$... |
| Wordlist Used | Built-in (100 passwords) | Built-in (100 passwords) |
| Password Found | ✅ **password1** | ✅ **1qaz2wsx** |
| PDF Opened | ✅ Yes | ✅ Yes |

---

## 💡 What I Learned

**1. How Hashing Works in Password-Protected Files**
When a PDF is locked, it does not store the password in plain text. It stores a hash — a fixed-length scrambled output produced by running the password through a one-way mathematical function. To crack it, the tool must find a word that produces the same hash.

**2. Dictionary Attack Mechanics**
The Password Cracker hashes each word in its wordlist one by one and compares the result to the target hash. When the hashes match, the original password is recovered. The built-in list of 100 common passwords was enough to crack both `password1` and `1qaz2wsx`.

**3. Keyboard Patterns Are Not Secure**
`1qaz2wsx` looks complex at a glance — it is 8 characters with mixed numbers and letters. However it is a well-known keyboard walking pattern (pressing Q-A-Z column then W-S-X column on a keyboard) and appears in every major password wordlist. It was cracked just as quickly as `password1`.

**4. Browser-Based Security Tools**
The Networkwalks tools run entirely client-side — no data is sent to any server. The Web Crypto API handles the hashing locally in the browser. This means the tools work on any device and any OS without installation.

**5. Encryption vs Hashing**
Encryption is reversible — the same key that locks the data can unlock it. Hashing is not reversible — the only way to recover the input is to guess it and check the hash. Password cracking is fundamentally a hash-guessing exercise.

---

## 🛡️ Password Strength Comparison

| Password | Type | Cracked? | Time |
|---|---|---|---|
| `password1` | Common word + digit | ✅ Yes | Seconds |
| `1qaz2wsx` | Keyboard pattern | ✅ Yes | Seconds |
| `Tr0ub4dor&3` | Mixed case + symbol | Unlikely with basic wordlist | Hours/days |
| `correct-horse-battery-staple` | 4-word passphrase | Very unlikely | Years+ |

---

## 📢 Do You Know?

- A simple 8-character lowercase password can be cracked in minutes; a strong 12-character mixed password can take many years.
- Over 24 billion username and password pairs are available on the dark web from past breaches.
- `123456` and `password` are still among the most used passwords in the world every year.
- In 2025, a leak of around 183 million Gmail login details showed how old stolen passwords keep circulating for years.

---

## 🔐 Security & Ethical Use

Both PDFs used in this module were provided by Networkwalks specifically for this educational exercise. Password cracking is only legal on files you own, files you have explicit written permission to test, or in authorized lab/CTF environments. Unauthorized use of these techniques is a criminal offence.

---

## 🔗 Tools & References

- **Networkwalks Hash Calculator:** [https://networkwalks.com/hash-calculator/](https://networkwalks.com/hash-calculator/)
- **Networkwalks Password Cracker:** [https://networkwalks.com/password-cracker/](https://networkwalks.com/password-cracker/)
- **Lab Page:** [https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/](https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/)

---

## 👤 Author

**Emmanuel Bafi**
Cybersecurity Intern — Batch B082
Networkwalks Cybersecurity Program | Week 3 | Project Module 2