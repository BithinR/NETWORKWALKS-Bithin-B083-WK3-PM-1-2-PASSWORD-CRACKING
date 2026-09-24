<div align="center">

# 🔐 Password Cracking with JTR

**W3-PM1 | Week 3 | Project Module 1**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Tool-John%20the%20Ripper-E87500?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Tool-Johnny%20GUI-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Platform-Windows-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Networkwalks-B082-404040?style=flat-square&labelColor=C00000" />
</p>

---

## 📌 Project Overview

This module covers **password cracking using John the Ripper (JTR)** — one of the most widely used password security auditing tools in cybersecurity. JTR supports hundreds of hash types and can unlock password-protected files including PDFs, ZIPs, and Office documents.

Two versions of the tool were used in this lab: **JTR John** (the command-line version) and **JTR Johnny** (the graphical GUI wrapper). Both were installed on a Windows PC and used to recover the password of a locked PDF file.

Understanding how password cracking works — and how quickly weak passwords are broken — demonstrates exactly why strong, complex passwords are essential for protecting sensitive files and accounts.

---

## 🎯 Objectives

- Download and install **John the Ripper** on Windows
- Download and install **Johnny GUI** on Windows
- Extract the hash from a password-protected PDF file
- Crack the PDF password using JTR John (CLI)
- Crack the PDF password using JTR Johnny (GUI)

---

## 🏗️ Lab Environment

| Component | Configuration |
|---|---|
| 🖥️ OS | Windows 10 (Host PC) |
| 🔧 Tool 1 | John the Ripper v1.9.0 (CLI) |
| 🔧 Tool 2 | Johnny GUI (graphical frontend for JTR) |
| 🎯 Target File | My Locked PDF1.pdf |
| 🔑 Password Found | **password1** |

---

## 🪜 Task Execution

---

### Step 1 — Download John the Ripper

Downloaded John the Ripper for Windows from the official source:

- Official: [https://www.openwall.com/john/](https://www.openwall.com/john/)
- Mirror: [https://distro.ibiblio.org/openwall/projects/john/1.9.0/](https://distro.ibiblio.org/openwall/projects/john/1.9.0/)

The download contains a `run/` folder with `john.exe` and all supporting files. No installation wizard is needed — just extract the ZIP to a folder.




---

### Step 2 — Download & Install Johnny GUI

Downloaded the Johnny graphical interface from:

- Official: [https://openwall.info/wiki/john/johnny](https://openwall.info/wiki/john/johnny)

Ran the Johnny setup file and completed the installation. After installation, opened Johnny for the first time.

**Configure Johnny to point to john.exe:**

In Johnny, clicked **Settings** → **Browse** and navigated to the `run/` folder extracted in Step 1, selected `john.exe`, and confirmed.



---

### Step 3 — Extract the PDF Hash

To crack a PDF password, the first step is to extract the password hash from the file. The hash is a scrambled representation of the password stored inside the PDF.

**Method used:** Uploaded the locked PDF to the online hash extractor:

[https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php)

1. Browsed to `My Locked PDF1.pdf` and clicked **Upload**.
2. The tool processed the file locally and returned a crackable hash value starting with `$pdf$...`
3. Copied the full hash value.




**Important:** Copy the complete hash starting from `$pdf$`. Do not include any extra characters such as `b'` at the beginning. The hash must be in the exact format: `$pdf$...`

**Saved hash to a text file:**

1. Opened Notepad.
2. Pasted the full hash value.
3. Saved the file as `password1.txt`.

---

### Task 1 — Crack with JTR Johnny (GUI)

**Step 4a: Load the hash file into Johnny**

1. Opened Johnny GUI.
2. Clicked **Open password file**.
3. Browsed to `hash1.txt` and clicked **Open** — the hash appeared in the password list.




**Step 4b: Start the attack**




**Step 4c: Password cracked**

Johnny found the match and displayed the recovered password.

**🔑 Password Cracked: `password1`**

---

### Task 2 — Verify by Opening the PDF

With the cracked password confirmed, opened `My Locked PDF1.pdf` in Adobe Acrobat Reader (or any PDF viewer). The file prompted for a password.

Entered: **`password1`**

The PDF unlocked and opened successfully.




---

## 📊 Summary of Results

| Item | Detail |
|---|---|
| Target File | My Locked PDF1.pdf |
| Hash Format | $pdf$ (PDF encryption hash, pdf2john compatible) |
| Tool Used (GUI) | JTR Johnny |
| Attack Method | Dictionary / Wordlist attack |
| Password Cracked | ✅ **password1** |
| Time to Crack | *3s* |
| PDF Successfully Opened | ✅ Yes |

---

## 💡 What I Learned

**1. Hashing vs Encryption**
Hashing is a one-way function — a password is converted to a hash, but the hash cannot be reversed directly. Password cracking works by hashing thousands of candidate words and comparing each result to the stored hash until a match is found.

Encryption is two-way — what is encrypted can be decrypted with the correct key. PDF password protection uses encryption, but the key is derived from the password via a hash, which is what JTR attacks.

**2. Dictionary Attacks**
JTR's default attack uses a wordlist — a large list of common passwords and words. It hashes each one and compares it to the target hash. `password1` was found quickly because it is a common, well-known password that appears near the top of most wordlists.

**3. Why Weak Passwords are Dangerous**
A simple, common password like `password1` was cracked in seconds. A well-crafted 12+ character password with mixed case, numbers, and symbols would take exponentially longer — potentially years or decades with current hardware.

**4. Johnny GUI vs JTR CLI**
Johnny provides a point-and-click interface that makes JTR accessible to beginners without requiring command-line knowledge. Under the hood it calls `john.exe` with the same arguments a command-line user would type. Both are equally effective.

**5. Real-world Relevance**
JTR is used by penetration testers during authorized security assessments to test password strength on recovered password databases, hash dumps, and protected files. The same technique is used by attackers on stolen credential databases from breaches.

---

## 🌍 Cybersecurity Facts

- **2026 — South Africa:** MTN Group's 2025 breach escalated in 2026; over 5,700 customers affected in Ghana alone, with criminal investigations opened across multiple countries.
- **2025 — Namibia:** Telecom Namibia refused to pay ransom; attackers leaked billing data of senior government officials.
- **2024 — Uganda:** Hackers broke into the Bank of Uganda and stole $16.8 million — one of Africa's largest ever banking cyber heists.
- **2024 — Nigeria:** Fintech giant Flutterwave was hacked and approximately $7 million was silently diverted from customer accounts.
- **2024 — South Africa:** Cell C breach exposed 2TB of data from 7.7 million customers, including ID numbers and banking details.

---

## 🔐 Security & Ethical Use

This lab was performed on a test PDF file provided by Networkwalks for educational purposes only. Password cracking is only legal when performed on files you own, files you have explicit written permission to test, or in a controlled lab/CTF environment. Unauthorized password cracking is a criminal offence in most jurisdictions.

---

## 🔗 Tools & References

- **John the Ripper:** [https://www.openwall.com/john/](https://www.openwall.com/john/)
- **Johnny GUI:** [https://openwall.info/wiki/john/johnny](https://openwall.info/wiki/john/johnny)
- **PDF Hash Extractor:** [https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php)
- **Kali Linux users:** JTR is pre-installed. Run `john --list=formats | grep pdf` to confirm PDF support.

---

## 👤 Author

**Bithin Krishna Radhakrishnan**
Cybersecurity Intern — Batch B083
Networkwalks Cybersecurity Program | Week 3 | Project Module 1
