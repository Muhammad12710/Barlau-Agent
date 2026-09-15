# BARLAU-AGENT | 🇰🇿
### BARLAU · Autonomous Reconnaissance Agent · Made in Kazakhstan

<img src="https://github.com/user-attachments/assets/9dde6e81-97dc-4b2a-afc7-9fafc010d4c4" alt="Barys Framework" width="700">

**Barlau** is an experimental Red Team tool for covert data exfiltration and
evasion of standard Windows endpoint protection. It was developed for
educational and research purposes to assess the resilience of corporate
security systems.

⚠️ **Warning:** This tool is intended **solely** for authorised penetration
tests, blue team training, and security demonstrations. The author
assumes **no liability** for any unauthorised use. This repository contains **demonstration materials
only**. The source code is **not public** and is shared exclusively
under NDA. Read the full [Disclaimer](DISCLAIMER.md).

---

## 🎯 Key Features

- 🕵️ **Silent extraction** of saved passwords and cookies from browsers
  (Chrome, Edge, and other Chromium-based).
- 📋 **System reconnaissance** – hostname, IP address, OS version, list
  of installed software.
- 📤 **Covert exfiltration** of harvested data to a Telegram bot(possibility to create a separate C2 in the future).
- 🧹 **Self-deletion** of the executable after execution (optional).
- 🛡️ **Evasion of Microsoft Defender** with default settings, Controlled
  Folder Access, and Tamper Protection (when cloud-based protection is
  disabled).
- 🔁 **Polymorphic build** – every compiled binary has a unique hash.
- 📦 **Single, portable EXE** – no Python installation required on the
  target machine.

---

## 🧠 How It Evades Defender

Barlau uses a combination of techniques to remain invisible to
Microsoft Defender:

1. **Polymorphic shellcode** – the core payload is XOR‑encrypted and
   injected with random NOP‑sleds, making static signatures useless.
2. **Deep obfuscation** – all strings and logic are mangled at build
   time, defeating heuristic analysis.
3. **Legitimate API behaviour** – no suspicious WinAPI calls (e.g.,
   `VirtualAllocEx`); the agent reads browser databases like any
   legitimate application.
4. **No AMSI footprint** – Python-based payloads are not scanned by
   AMSI, bypassing script-level inspection.
5. **HTTPS exfiltration** – data is sent to `api.telegram.org` over
   TLS, blending into normal network traffic.
6. **Self-deletion** – the agent removes itself from disk after
   execution, eliminating forensic evidence.

---

## 📸 Demonstration
