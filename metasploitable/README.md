# 🧱 Metasploitable – VulnHub Walkthrough

Metasploitable is an intentionally vulnerable Linux-based virtual machine designed for testing and developing exploits. It contains a wide range of vulnerable services that simulate real-world attack surfaces, making it an excellent starting point for beginners in penetration testing and ethical hacking.

---

## 📦 Machine Details

- **Name**: Metasploitable 2
- **Platform**: Linux (Ubuntu-based)
- **Download**: [https://sourceforge.net/projects/metasploitable/](https://sourceforge.net/projects/metasploitable/)
- **Difficulty**: 🟢 Beginner
- **Goal**: Gain shell access and root the machine
- **IP Address**: Automatically assigned via DHCP (discovered with netdiscover or nmap)

---

## 🎯 Key Learning Objectives

- Nmap scanning and full port discovery
- Enumeration of common services (FTP, SSH, HTTP, Telnet, etc.)
- Exploiting known vulnerabilities using Metasploit and manual methods
- Gaining shell access via vulnerable services like VSFTPD, Tomcat, Samba, etc.
- Privilege escalation using Linux misconfigurations and post-exploitation tools

---

## 🛠️ Tools Used

- `nmap`
- `netdiscover`
- `hydra`
- `gobuster` / `dirb`
- `metasploit-framework`
- `nikto`
- `searchsploit`
- `msfvenom`
- `LinPEAS`, `Linux Exploit Suggester`

---

## 🧩 Walkthrough Breakdown

| Phase                    | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| [`reconnaissance.md`](./reconnaissance.md)       | Discover the target machine and its open ports using tools like netdiscover and nmap |
| [`enumeration.md`](./enumeration.md)             | Deep service enumeration (FTP, SSH, HTTP, Samba, etc.) to identify potential entry points |
| [`exploitation.md`](./exploitation.md)           | Exploit multiple services using Metasploit and/or manual techniques |
| [`privilege-escalation.md`](./privilege-escalation.md) | Escalate privileges from limited user to root using local vulnerabilities |
| [`flags.md`](./flags.md)                         | Document user and root flags captured during the engagement |

---

## 📌 Notable Vulnerable Services

- **FTP**: vsftpd 2.3.4 (backdoor vulnerability)
- **Telnet**: Accessible with known default credentials
- **Samba**: Null session enumeration and exploitation
- **Tomcat Manager**: Remote deployment of WAR reverse shell
- **MySQL**: Weak or no authentication
- **DistCC**: Remote code execution
- **PHPMyAdmin / WebDAV / Mutillidae / TWiki / DVWA**: Multiple web-based exploits

---

## ⚠️ Disclaimer

> This machine is designed for **educational use only**. Do not attempt to exploit real-world systems without proper authorization. All actions performed in this write-up were done in a legal, isolated, and controlled lab environment.

---

## ✅ Status

- [x] Reconnaissance
- [x] Enumeration
- [x] Exploitation
- [x] Privilege Escalation
- [x] Rooted Successfully
