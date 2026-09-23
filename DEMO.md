# 🧪 Demo — Laboratory Walkthrough

## 1. Defender Active

<img width="1920" alt="Defender Active" src="https://github.com/user-attachments/assets/6127ad06-eb45-4d12-8c88-745179a4bfd0" />

> The standard protection(Windows Defender) is active. No exceptions have been added. 
>  
> **Note:** The current agent successfully bypasses built-in Windows defences; however, enterprise-grade EDR/XDR solutions, application whitelisting, and other host-based intrusion prevention systems may require environment-specific tailoring. Custom payload delivery, in‑memory execution chains, and EDR‑aware evasion techniques are under active development for future releases.

## 2. Agent on desktop
<img width="1920" height="983" alt="Barlau" src="https://github.com/user-attachments/assets/f9973e60-aa5d-40f9-94a2-3ff96af00dd8" />

> The agent has been delivered. A regular executable file that does not require installation. Launching our program.

## 3. Data Exfiltration - Barlau Telegram Bot

<img width="1313" height="830" alt="Telegram_bot" src="https://github.com/user-attachments/assets/790f0734-68c6-48d5-a734-ef07f98c065f" />

> The data is sent in chunks, then collected with a single command and password, the password is random for the zip archive. In the experimental prototype, data is transmitted via a Telegram bot API as a lightweight, readily deployable channel. This approach serves as a temporary proof-of-concept to validate end-to-end delivery, encryption, and segmented transfer within controlled laboratory environments. Next iteration: A dedicated, self-hosted command-and-control server is under active development. The server will support mutual TLS authentication, encrypted data ingestion over HTTPS, and a web-based dashboard for real-time tasking and report aggregation. This will replace the Telegram bot in production-ready releases, ensuring full operational sovereignty and compliance with internal security policies.

## 4. Data Collected

<img width="1606" height="688" alt="Data" src="https://github.com/user-attachments/assets/1623c44f-c5fc-453c-a734-98159642e361" />

> Assembling an archive from parts. The key was received separately.

## 5. Extracted data

> ⚠️ **Disclaimer:** All files shown are synthetic dummy data created in an isolated laboratory environment. Actual harvested data will vary depending on the target system, installed software, user behaviour, and local file landscape.

https://github.com/user-attachments/assets/7b158471-ce28-4778-957b-3cfe7bfcb7b5

> After a single run, the agent collected over 150 files — a complete digital fingerprint of the user.  Harvested artefacts include:

- **Decrypted browser passwords** from Chrome, Edge, Brave (sample: `kz.mil@gmail.com : S3cr3tP@ss`).
- **Full browsing history & bookmarks**.
- **System intelligence** – OS, hardware, active AV, Wi‑Fi profiles with pre‑shared keys, etc.
- **Real‑time session data** – 60‑second keylog, clipboard dump (often containing passwords or seed phrases), screenshot of the desktop.
- **Sensitive documents** – thesis chapters (DH-Chapter1–7), immigration forms (IMM5756), language certificates, penetration test reports (`Iron Corp pentest`, `HTB-CPTS-Report`), and a personal diary.
- **Professional certifications** – Coursera, THM, HTB, KC7, revealing the target’s defence skill set.

> **Why it matters:** Barlau doesn't just grab credentials — it builds an exhaustive intelligence dossier, giving an attacker full context on the victim’s work, studies, and identity.

In future releases, the agent will be enhanced with environment‑specific evasion (EDR/XDR), configurable collection filters, and a dedicated, self‑hosted C2 infrastructure to replace the temporary Telegram channel currently used for demonstration purposes.

## 6. Stealth & Self-Destruct
<img width="1312" height="1199" alt="evasion" src="https://github.com/user-attachments/assets/5624141f-e0bb-4c4f-812d-ae9486897fec" />

> After exfiltration, the agent performs a silent cleanup:

- **Log wiping:** All Windows Event Logs (Security, System, Application, Sysmon) are cleared via `wevtutil cl`, removing any trace of process creation, privilege escalation, or file access.
- **Artifact removal:** The temporary working directory (`%TEMP%\Barl_xxxx`) is shredded and deleted.
- **Self-deletion:** The original executable schedules its own deletion via a delayed batch command or direct `DeleteFileW` after process termination.

**Result:** The target system returns to its pre-infection state. Defender shows no alerts, Event Viewer is empty, and the user's TEMP folder is clean. For an IT administrator, nothing happened.
