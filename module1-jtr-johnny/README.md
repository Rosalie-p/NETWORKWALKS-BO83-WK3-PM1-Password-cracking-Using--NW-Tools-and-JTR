# Module 1 — Password Cracking with John the Ripper (JTR) + Johnny GUI

Week 3 | Project Module 1 — Networkwalks Cybersecurity & Ethical Hacking

## Objective

Crack the password of the attached PDF file (`My Locked PDF1.pdf`) using
JTR John and JTR Johnny on a Windows PC. Extended in this run to also
cover two additional locked files, `My Locked PDF2.pdf` and
`My Locked PDF3.pdf`, cracked together in a single combined attack.

## Tools

- **John the Ripper (jumbo)** — 1.9.0-jumbo-1, 64-bit Windows binaries
  Download: https://www.openwall.com/john/ or
  https://distro.ibiblio.org/openwall/projects/john/1.9.0/
- **Johnny** (GUI front end for JTR) — v2.2, Windows binaries
  Download: https://openwall.info/wiki/john/johnny
- **Online Hash Extractor** (to convert the PDF into a crackable hash):
  https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php

## Steps performed

1. **Installed John the Ripper.** Extracted the jumbo 64-bit Windows
   archive. The executable (`john.exe`, shown as `john` with extensions
   hidden) is located at:
   `...\john-1.9.0-jumbo-1-win64\run\john.exe`

2. **Installed Johnny.** Downloaded and ran `johnnyInstaller.exe`, then
   launched Johnny from the Start Menu.

3. **Linked Johnny to John.** In Johnny: **Settings → Browse** → selected
   `john.exe` from the `run` folder. Johnny confirmed detection:
   `Detected John the Ripper 1.9.0-jumbo-1 OMP [cygwin 64-bit x86_64 AVX2 AC]`

4. **Extracted the PDF hashes.** Uploaded each of `My Locked PDF1.pdf`,
   `My Locked PDF2.pdf`, and `My Locked PDF3.pdf` to the online hash
   extractor in turn, which returned a `pdf2john`-format hash for each,
   starting with `$pdf$4*4*128*...`. Copied each full hash value (verified
   no stray `b'` prefix).

5. **Saved the hashes.** Pasted all three hashes into Notepad/Notepad++,
   one per line, and saved as a single combined file (`hash1.txt`), noting
   which line corresponded to which source filename.

6. **Loaded the hashes into Johnny.** **Open password file** → selected
   the combined hash file. Three rows appeared, each with format `PDF`.

7. **Ran the attack.** Clicked **Start new attack**. Johnny/John ran its
   default wordlist and rules against all three hashes in a single pass.

8. **Result.** Status bar showed `100% (3/3: 3 cracked, 0 left)
   [format=PDF]`. The **Passwords** tab displayed all three cracked
   values.

9. **Verified.** Opened each locked PDF in Adobe Acrobat Reader, entered
   its recovered password, and confirmed each file unlocked successfully.

## Result

| # | Target file | Cracked password |
|---|---|---|
| 1 | `My Locked PDF1.pdf` | `good-luck` |
| 2 | `My Locked PDF2.pdf` | `password1` |
| 3 | `My Locked PDF3.pdf` | `1qaz2wsx` |

All three hashes used the `$pdf$4*4*128*...` format (pdf2john /
hashcat-compatible) and were cracked in one combined run using JTR's
default wordlist and mangling rules.

**Flag captured (PDF1):** `nw{networkwalks_flag1_jtr_270521_1}`

## Notes / troubleshooting encountered

- Windows hides file extensions by default, so `john.exe` displayed as
  `john` in File Explorer — this is expected and not a missing-file issue.
- After a successful crack, the result is visible on the **Passwords**
  tab in Johnny, not on the **Settings** tab — easy to miss if you're
  still looking at the executable-path screen.

## Scaling to multiple files

As demonstrated above, multiple `$pdf$...` hashes can be combined into a
single text file (one hash per line, no blank lines) and loaded into
Johnny in one pass — Johnny attacks all rows in the same run, which is
significantly faster than repeating the full workflow per file.
