# NETWORKWALKS-BO83-WK3-PM1-Password-cracking-Using--NW-Tools-and-JTR
# Password Cracking Labs — Week 3 Project

**Course:** Networkwalks Cybersecurity & Ethical Hacking Training
**Module:** Week 3 — Project Modules 1 & 2
**Target files:** `My Locked PDF1.pdf`, `My Locked PDF2.pdf`, `My Locked PDF3.pdf`
**Author:** [Your Name]
**Date:** [Date]

## Overview

This repo documents two lab exercises that recover passwords from locked
PDF files using two different tool sets. Both exercises follow the same
underlying workflow:

1. Extract a crackable hash from the PDF (`pdf2john` format: `$pdf$...`)
2. Run a dictionary attack against that hash
3. Use the recovered password to open the PDF

| Module | Tools used | Scope | Folder |
|---|---|---|---|
| 1 | John the Ripper (JTR) + Johnny GUI | All 3 files (combined hash attack) | [`module1-jtr-johnny/`](./module1-jtr-johnny) |
| 2 | Networkwalks Hash Calculator + Password Cracker (web-based) | `My Locked PDF1.pdf` only | [`module2-networkwalks-tools/`](./module2-networkwalks-tools) |

A combined write-up of both modules is in [`report/`](./report) as a Word
document suitable for submission.

## Results

| # | Target file | Module | Cracked password | Flag captured |
|---|---|---|---|---|
| 1a | `My Locked PDF1.pdf` (Module 1's copy) | Module 1 (JTR) | `good-luck` | `nw{networkwalks_flag1_jtr_270521_1}` |
| 1b | `My Locked PDF1.pdf` (Module 2's copy) | Module 2 (Networkwalks) | `password1` | `nw{cybersecurity_flag_captured_2608}` |
| 2 | `My Locked PDF2.pdf` | Module 1 (JTR) | `password1` | — |
| 3 | `My Locked PDF3.pdf` | Module 1 (JTR) | `1qaz2wsx` | — |

**Note:** Module 1 and Module 2 each bundle their own file named
`My Locked PDF1.pdf` — these are two distinct files that happen to share
a filename, not the same file with two different results. Each cracked
correctly to its own password and its own unique flag, confirming both
results are valid.

## Ethical note

This exercise was performed only against a training file provided by the
course, for learning purposes. Password-cracking tools and techniques shown
here should only ever be used on systems and files you own or have explicit
written authorization to test.

## Repo structure

```
password-cracking-labs/
├── README.md                        ← you are here
├── module1-jtr-johnny/
│   └── README.md
├── module2-networkwalks-tools/
│   └── README.md
└── report/
    └── Password-Cracking-Lab-Report.docx
```
