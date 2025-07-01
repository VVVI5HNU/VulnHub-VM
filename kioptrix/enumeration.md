🕵️ Enumeration – Kioptrix Level 1

In this phase, we perform detailed analysis of open services to find weaknesses that could lead to exploitation.

---

## 📟 1. Port 22 – SSH (OpenSSH 2.9p2)

This is an older version of OpenSSH (circa 2001) running on FreeBSD. No immediate exploit available, but brute-force attacks might succeed if weak credentials are in use.

> Save for post-exploitation access after credential discovery.

---

## 🌐 2. Port 80 – Apache 1.3.20

Very old version of Apache. Likely contains multiple web application vulnerabilities.

### ➤ Access via Browser
Go to:
```

[http://192.168.1.110](http://192.168.1.110)

````

Homepage contains:
- Static Apache test page
- No forms or login interfaces visible

---

### ➤ Run Nikto
```bash
nikto -h http://192.168.1.110
````

✅ Output:

* `PHP/4.3.10` detected
* Potential file upload found
* Apache version susceptible to multiple buffer overflows and XSS

---

### ➤ Run Dirb / Gobuster

```bash
gobuster dir -u http://192.168.1.110 -w /usr/share/wordlists/dirb/common.txt
```

✅ Findings:

* `/test.php`
* `/phpinfo.php`
* `/manual/`
* `/index.html`

📌 Pay special attention to test pages like `test.php` and `phpinfo.php` — often exposed in development environments.

---

## 🧾 3. Port 111 – RPCBind

### ➤ Nmap RPC Scripts

```bash
nmap -sV --script=rpcinfo -p 111 192.168.1.110
```

✅ Output:

* RPC services are running
* Might indicate **NFS** or other RPC-based services

### ➤ Enumerate RPC Programs

```bash
rpcinfo -p 192.168.1.110
```

> If NFS is found, list exports with:

```bash
showmount -e 192.168.1.110
```

---

## 🧠 Summary of Interesting Targets

| Port | Service | Notes                                                          |
| ---- | ------- | -------------------------------------------------------------- |
| 80   | Apache  | Old version, vulnerable. Found `/test.php`, may be injectable. |
| 111  | RPCBind | NFS or RPC services may be misconfigured.                      |
| 22   | SSH     | Target for brute-force or post-exploitation access.            |

---

📂 Proceed to [`exploitation.md`](./exploitation.md) to exploit the Apache service and gain a foothold on the machine.
