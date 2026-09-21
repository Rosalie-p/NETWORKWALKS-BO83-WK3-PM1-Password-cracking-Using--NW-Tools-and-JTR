# Module 2 — Password Cracking with Networkwalks Tools

Week 3 | Project Module 2 — Networkwalks Cybersecurity & Ethical Hacking

## Objective

Crack the password of `My Locked PDF1.pdf` using two free, browser-based
Networkwalks tools instead of installing local software.

## Tools

- **Networkwalks Hash Calculator** — https://networkwalks.com/hash-calculator/
  Extracts a `pdf2john`/hashcat-compatible hash from a locked PDF, entirely
  client-side (no upload to a server).
- **Networkwalks Password Cracker** — https://networkwalks.com/password-cracker/
  Runs a dictionary attack against a pasted `$pdf$...` hash, either using a
  built-in 100-word list or an uploaded custom wordlist.

## Steps performed

1. **Downloaded the target file** — `My Locked PDF1.pdf` — from the course
   lab page.

2. **Extracted the hash.** Opened the Hash Calculator, selected the **PDF**
   tab, and uploaded `My Locked PDF1.pdf`. The tool parsed the file locally
   in-browser and returned a hash beginning `$pdf$4*4*128*-1060*1*16*...`.

3. **Copied the full hash**, taking care to copy the complete string
   starting from `$pdf$`.

4. **Ran the Password Cracker.** Opened the Password Cracker tool, pasted
   the hash into the **PDF Hash** field, confirmed the **Built-in list
   (100 passwords)** was active, and clicked **Start Cracking**.

5. **Result.** The tool displayed **"PASSWORD CRACKED SUCCESSFULLY"** with
   the recovered value.

6. **Verified.** Opened `My Locked PDF1.pdf`, entered the password, and the
   file unlocked, displaying the course's flag-capture confirmation page.

## Result

| Item | Value |
|---|---|
| Target file | `My Locked PDF1.pdf` |
| Hash format | `$pdf$4*4*128*-1060*1*16*...` |
| Attack type | Built-in 100-word dictionary list |
| **Cracked password** | **`password1`** |
| **Flag captured** | `nw{cybersecurity_flag_captured_2608}` |

Matches the result independently obtained in Module 1 (JTR + Johnny),
confirming the password.

## Notes / troubleshooting encountered

- Early on, a hash from a **different** PDF was mistakenly pasted into the
  Password Cracker, which correctly returned **"Access Denied — Not
  cracked with this wordlist. Load a larger wordlist and run the attack
  again"** since that file's password wasn't in the 100-word built-in
  list. Re-extracting and re-pasting the correct hash for `My Locked
  PDF1.pdf` resolved this.
- Takeaway: when working with several locked files at once, label or
  keep track of which hash belongs to which filename before pasting into
  the cracker — the tool has no way to know this for you.

## Comparison with Module 1

Module 1 and Module 2 each ship their **own copy** of a file named
`My Locked PDF1.pdf` — they are two distinct files that happen to share
a filename (one bundled with each module's lab materials), not the same
file cracked twice. Each has its own password and its own unique flag:

| | Module 1 (JTR + Johnny) | Module 2 (Networkwalks Tools) |
|---|---|---|
| Install required | Yes (JTR + Johnny) | No — runs in browser |
| Hash extraction | Third-party online extractor | Networkwalks Hash Calculator |
| Cracking engine | John the Ripper (local) | Networkwalks Password Cracker (browser) |
| Wordlist | JTR default wordlist + rules | Built-in 100-word list |
| **PDF1 password** | **`good-luck`** | **`password1`** |
| **Flag captured** | `nw{networkwalks_flag1_jtr_270521_1}` | `nw{cybersecurity_flag_captured_2608}` |

The two different passwords are expected, not an error — confirmed by
each file opening to a distinct, correctly formatted flag page.
