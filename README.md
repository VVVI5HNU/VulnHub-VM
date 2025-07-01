# VulnHub-VM
# 🧱 VulnHub Machine Walkthroughs

This repository contains structured, step-by-step walkthroughs of intentionally vulnerable virtual machines from [VulnHub](https://www.vulnhub.com/). These are aimed at practicing real-world penetration testing, vulnerability assessment, and privilege escalation techniques in a legal and controlled environment.

---

## 📦 Covered Machines

| Machine        | Difficulty | Key Concepts Covered                               |
|----------------|------------|----------------------------------------------------|
| [Metasploitable](./metasploitable/) | Beginner   | Service enumeration, MSF usage, misconfigurations  |
| [Kioptrix](./kioptrix/)             | Beginner   | Web attacks, file inclusion, privilege escalation  |
| [Mr. Robot](./mr-robot/)            | Intermediate | CTF-style enumeration, WordPress exploits, manual post-exploitation |

---

## 🧰 Tools & Techniques Used

- **Network Scanning**: `nmap`, `netdiscover`
- **Web Enumeration**: `nikto`, `gobuster`, `whatweb`
- **Password Attacks**: `hydra`, `John the Ripper`
- **Exploitation**: `Metasploit Framework`, manual payloads, PHP/Python reverse shells
- **Privilege Escalation**: `LinPEAS`, `sudo`, weak permissions, cron jobs
- **CTF Enumeration**: Hidden files, Base64 decoding, steganography (Mr. Robot)

---

## 📁 Folder Structure

Each machine contains the following:
machine-name/
├── README.md               # Overview of the machine
├── reconnaissance.md       # Network discovery and scanning
├── enumeration.md          # In-depth service and web enumeration
├── exploitation.md         # Initial access / vulnerability exploitation
├── privilege-escalation.md # PrivEsc to root
└── flags.md                # Captured user/root flags (if any)


---

## 🛡️ Legal Disclaimer

> All activities documented here were performed in a safe, local lab environment for educational purposes only. Do not attempt these techniques on systems you do not own or have permission to test.

---

Happy hacking! ⚔️
