🔍 Reconnaissance – Metasploitable

This phase involves identifying the target machine's IP address and discovering its open ports and running services. This sets the stage for deeper enumeration and exploitation.

---

## 🌐 1. Discover the Target's IP Address

Assuming you're in a local lab environment using VirtualBox or VMware in bridged or NAT mode.

### 🔎 Using `netdiscover`
```bash
sudo netdiscover -r 192.168.1.0/24
````

Look for a Linux host (MAC vendor often shows as "00:0C:29" or "VMware, Inc.").

✅ Example output:

```
192.168.1.109   00:0c:29:ab:cd:ef   1   60   VMware, Inc.
```

> We'll use `192.168.1.109` as the target IP throughout this walkthrough.

---

## 🔬 2. Basic Nmap Scan

Use a default safe scan to identify open ports and service versions.

```bash
nmap -sC -sV -oN nmap-basic.txt 192.168.1.109
```

✅ Key Flags:

* `-sC`: Use default scripts
* `-sV`: Detect service versions
* `-oN`: Save output to file

---

## 🚪 3. Full TCP Port Scan

Metasploitable has many services exposed. A full port scan is necessary.

```bash
nmap -p- -T4 -oN nmap-full.txt 192.168.1.109
```

✅ `-p-`: Scan all 65535 ports
✅ `-T4`: Increase speed

> Review `nmap-full.txt` and note ports not discovered in the initial scan.

---

## 📑 Sample Output Summary

Example ports discovered:

```
PORT      STATE SERVICE     VERSION
21/tcp    open  ftp         vsftpd 2.3.4
22/tcp    open  ssh         OpenSSH 4.7p1 Debian
23/tcp    open  telnet      Linux telnetd
25/tcp    open  smtp        Postfix smtpd
80/tcp    open  http        Apache httpd 2.2.8
3306/tcp  open  mysql       MySQL 5.0.51a
8180/tcp  open  http        Apache Tomcat/Coyote JSP engine 1.1
139/tcp   open  netbios-ssn Samba smbd 3.X
445/tcp   open  microsoft-ds Samba smbd 3.X
```

---

## 🧠 What to Note for Next Phase

* Check which services run on which ports (FTP, Telnet, Samba, etc.)
* Highlight weak versions (e.g., vsftpd 2.3.4 is **known vulnerable**)
* Check all web-facing ports for HTTP services (80, 8180, etc.)
