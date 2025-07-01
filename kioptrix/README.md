# 🛡️ Kioptrix – VulnHub Walkthrough

Kioptrix Level 1 is part of a series of intentionally vulnerable virtual machines designed to test and advance your penetration testing skills. This machine simulates real-world scenarios and teaches the importance of proper system hardening.

---

## 📦 Machine Details

- **Name**: Kioptrix Level 1
- **Platform**: Linux (FreeBSD variant)
- **Download**: [https://www.vulnhub.com/entry/kioptrix-level-1-1,22/](https://www.vulnhub.com/entry/kioptrix-level-1-1,22/)
- **Difficulty**: 🟢 Beginner
- **Goal**: Gain root access
- **IP Address**: Discovered via network scan

---

## 🎯 Key Learning Objectives

- Network discovery and fingerprinting
- Exploiting vulnerable web applications and services
- Gaining shell access using known exploits
- Privilege escalation via kernel-level vulnerabilities

---

## 🛠️ Tools Used

- `nmap`
- `netdiscover`
- `Nikto`
- `searchsploit`
- `Metasploit`
- `gcc`, `wget`, `python`
- `LinPEAS` / `uname` / `id` / `sudo -l`

---

## 🧩 Walkthrough Breakdown

| Phase                    | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| [`reconnaissance.md`](./reconnaissance.md)       | Discover the target machine and identify open ports and services      |
| [`enumeration.md`](./enumeration.md)             | Deep dive into services (Apache, MySQL, etc.) and find weaknesses     |
| [`exploitation.md`](./exploitation.md)           | Exploit discovered vulnerabilities to gain user access                |
| [`privilege-escalation.md`](./privilege-escalation.md) | Escalate privileges and gain root                                     |
| [`flags.md`](./flags.md)                         | Document captured root flag                                           |

---

## 🔍 Notable Services

- Apache 1.3.x
- OpenSSH 2.9p2
- MySQL 3.23.49
- PHP 4.3.10

---

## ⚠️ Disclaimer

> This virtual machine is designed for educational purposes only. All tests were conducted in a legal and isolated environment.

---

## ✅ Status

- [x] Reconnaissance
- [x] Enumeration
- [x] Exploitation
- [x] Privilege Escalation
- [x] Rooted Successfully
