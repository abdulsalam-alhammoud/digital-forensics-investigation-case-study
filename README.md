# Digital Forensics Investigation — Case Study 4321

**University:** Deggendorf Institute of Technology (TH Deggendorf)  
**Degree:** B.Sc. Cyber Security  
**Module:** Digitale Forensik (Digital Forensics)  
**Case:** 4321 — Fictional kidnapping investigation (Rosanna Lorenzo)

## Overview

A team-based academic digital forensics investigation conducted in a **simulated criminal case**. The team created and examined digital evidence from a virtual Ubuntu system, a memory acquisition, and an encrypted virtual USB container. The objective was to follow a reproducible, evidence-led forensic workflow, preserving integrity and reconstructing a timeline from independent artifacts.

## My contribution

**Abdusalam Alhammoud — forensic analysis (40% of team workload)**

- Disk and filesystem examination, including partition offsets and ext4 artifacts
- Recovery of deleted files using content-based carving
- Volatile-memory analysis and investigation of credentials and command history
- Analysis of steganography, image metadata, and encrypted evidence
- Correlation of recovered artifacts into an investigative timeline

The division of responsibilities in the report attributes case design and evidence preparation to **Shahed Al Hendi (40%)**, forensic analysis to **Abdusalam Alhammoud (40%)**, and documentation to **Janine Heinl (20%)**.

## Forensic workflow

1. **Evidence acquisition and integrity:** FTK Imager for raw disk images, AVML for a compressed LiME memory image, and hash verification.
2. **Disk analysis:** The Sleuth Kit (`mmls`, `fsstat`, `fls`, `icat`) to inspect GPT partitions, the ext4 filesystem, user profiles, shell history, and cron jobs.
3. **Deleted-file recovery:** A custom Python carving script (`carve_deleted.py`) recovered a JSON chat history (24 messages) and location log (30 entries) from unallocated space.
4. **Memory forensics:** Volatility 3 and `strings` to examine volatile evidence and derive candidate credentials for verification.
5. **Specialized artifact analysis:** `exiftool` for GPS metadata, `steghide` for concealed content, and `cryptsetup`/LUKS for an encrypted virtual USB container.
6. **Evidence correlation:** Reconstructed the chronology, compared independent artifacts, and documented chain of custody.

## Tools

| Category | Tools |
| --- | --- |
| Acquisition | FTK Imager, AVML |
| Filesystem analysis | The Sleuth Kit |
| Memory analysis | Volatility 3, GNU strings |
| File recovery | Python (custom carving script) |
| Metadata and steganography | ExifTool, steghide |
| Encryption and verification | cryptsetup/LUKS, John the Ripper, OpenSSL |
| Integrity verification | Hashing tools (MD5, SHA-1, SHA-256) |

## Key results

- Identified the Linux partition in the forensic disk image and analyzed its ext4 filesystem.
- Recovered two intentionally deleted artifacts through carving rather than filename-based undelete.
- Analyzed shell history, scheduled tasks, and recent-file references to guide subsequent examination.
- Correlated location records with embedded image GPS metadata.
- Investigated volatile memory and encrypted evidence to reconstruct the simulated case.

## Documentation and scope

The full university report is titled **Forensischer Bericht — Fall 4321** (34 pages). It describes the methodology, screenshots, artifacts, integrity checks, findings, and limitations.

**This is a fictional educational investigation, not a real criminal case.** Any people, events, credentials, and evidence described in the case are part of the simulation.

The report contains student identification numbers and example passwords; the original PDF is not included in this public repository pending a privacy review. If a redacted copy is later published, it can be linked here.

**Supervisor:** Prof. Dr. Michael Heigl.

## Reproducibility

The report references additional forensic artifacts and a custom carving script that are **not currently included** in this repository. The README summarizes the documented investigation; it does not claim that the original forensic images or scripts are available here.
