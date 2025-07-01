🕵️ Enumeration – Metasploitable

In this phase, we perform deep enumeration of the services discovered during reconnaissance. This helps us identify vulnerabilities and potential attack vectors.

---

## 🔐 1. FTP (Port 21)

### ➤ Banner Grabbing
```bash
telnet 192.168.1.109 21
````

> Service: `vsftpd 2.3.4`
> ⚠️ Vulnerable to a known backdoor — will be exploited later.

---

## 🖥️ 2. SSH (Port 22)

```bash
nmap -p 22 --script ssh2-enum-algos 192.168.1.109
```

> Nothing immediately exploitable. Brute-force may work if credentials are found later.

---

## 📟 3. Telnet (Port 23)

```bash
telnet 192.168.1.109
```

Try default logins:

* `msfadmin:msfadmin`
* `user:user`
* `root:toor`

✅ Successful login with `msfadmin:msfadmin`.

---

## 🌐 4. HTTP (Port 80)

### ➤ Access in Browser

Visit: [http://192.168.1.109](http://192.168.1.109)

* Contains multiple web apps:

  * **DVWA** – Damn Vulnerable Web App
  * **Mutillidae**
  * **phpMyAdmin**
  * **TWiki**
  * **WebDAV**

### ➤ Directory Brute-Force

```bash
gobuster dir -u http://192.168.1.109 -w /usr/share/wordlists/dirb/common.txt
```

### ➤ Nikto Scan

```bash
nikto -h http://192.168.1.109
```

---

## 🧾 5. SMTP (Port 25)

```bash
telnet 192.168.1.109 25
```

Try VRFY to enumerate users:

```bash
VRFY msfadmin
VRFY root
```

---

## 🗃️ 6. Samba (Ports 139, 445)

### ➤ Null Session Enum

```bash
enum4linux -a 192.168.1.109
```

✅ Results:

* Users: `msfadmin`, `user`, `root`
* Shares: `tmp`, `public`, etc.

### ➤ Nmap Samba Scripts

```bash
nmap --script smb-enum-shares,smb-enum-users -p 139,445 192.168.1.109
```

---

## 🧩 7. Tomcat (Port 8180)

Visit: [http://192.168.1.109:8180](http://192.168.1.109:8180)

### ➤ Default Credentials

Try:

* `tomcat:tomcat`
* `admin:admin`
* `admin:tomcat`

If login succeeds, deploy a reverse shell WAR file later in exploitation.

---

## 🗃️ 8. MySQL (Port 3306)

Test with:

```bash
mysql -u root -h 192.168.1.109 -p
```

> May not be exploitable directly, but will be useful if creds are dumped from web apps.

---

## 📌 Summary of Interesting Findings

| Service | Key Info / Vulnerability                              |
| ------- | ----------------------------------------------------- |
| FTP     | vsftpd 2.3.4 — Backdoor vulnerability                 |
| Telnet  | Default login works (`msfadmin`)                      |
| HTTP    | Multiple vulnerable web apps (DVWA, phpMyAdmin, etc.) |
| Samba   | Null session enabled — enum4linux successful          |
| Tomcat  | Admin panel exposed on port 8180                      |

---
