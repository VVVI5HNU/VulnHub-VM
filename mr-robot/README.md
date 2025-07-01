👨‍💻 Mr. Robot – VulnHub Walkthrough

Mr. Robot is a CTF-style vulnerable VM hosted on VulnHub. It’s themed after the popular TV show "Mr. Robot" and provides a fun and realistic hacking scenario that simulates a compromised WordPress website and privilege escalation to root.

---

## 📦 Machine Details

- **Name**: Mr. Robot
- **Platform**: Linux (Debian-based)
- **Download**: [https://www.vulnhub.com/entry/mr-robot-1,151/](https://www.vulnhub.com/entry/mr-robot-1,151/)
- **Difficulty**: 🟡 Intermediate
- **Goal**: Capture the 3 hidden flags and gain root access
- **IP Address**: Determined via scanning

---

## 🎯 Objectives

- Discover 3 hidden flags
- Gain shell access via WordPress exploitation
- Escalate privileges to root

---

## 🛠️ Tools Used

- `nmap`
- `gobuster`
- `wpscan`
- `hydra`
- `Metasploit`
- `python`, `netcat`, `john`, `hashcat`

---

## 🧩 Walkthrough Structure

| Phase                     | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| [`reconnaissance.md`](./reconnaissance.md)         | Identify open ports and services                                              |
| [`enumeration.md`](./enumeration.md)               | Enumerate WordPress, users, and directories                                  |
| [`exploitation.md`](./exploitation.md)             | Exploit vulnerable services and gain shell access                            |
| [`privilege-escalation.md`](./privilege-escalation.md)   | Escalate from user to root                                                    |
| [`flags.md`](./flags.md)                           | Record of all captured flags and final root confirmation                     |

---

## ⚠️ Notes

- The machine has multiple hidden files and directories.
- WordPress is the main attack vector.
- Password reuse and hashing are key parts of exploitation.

---

## ✅ Status

- [x] Reconnaissance
- [x] Enumeration
- [x] Exploitation
- [x] Privilege Escalation
- [x] All Flags Captured

---

📂 Begin with [`reconnaissance.md`](./reconnaissance.md) for host discovery and port scanning.
