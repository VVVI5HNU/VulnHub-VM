🔍 Reconnaissance – Mr. Robot

The goal of this phase is to identify the IP address of the Mr. Robot VM and scan for open ports and services running on the target.

---

## 🌐 1. Identify Target IP

Assuming the VM is on the same local network.

### ➤ Using `netdiscover`
```bash
sudo netdiscover -r 192.168.1.0/24
````

✅ Output:

```
192.168.1.105   00:0C:29:XX:XX:XX   1   60   VMware, Inc.
```

> The Mr. Robot VM is running on IP: `192.168.1.105` (example).

---

## 🔎 2. Basic Nmap Scan

```bash
nmap -sC -sV -oN nmap-basic.txt 192.168.1.105
```

✅ Sample output:

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 6.0p1 Debian 4+deb7u2
80/tcp open  http    Apache httpd 2.4.7 ((Ubuntu))
```

---

## 🚪 3. Full Port Scan

```bash
nmap -p- -T4 -oN nmap-full.txt 192.168.1.105
```

Only ports 22 and 80 are usually open on this machine.

---

## 🧠 Observations

| Port | Service | Notes                               |
| ---- | ------- | ----------------------------------- |
| 22   | SSH     | Could be used for post-exploitation |
| 80   | HTTP    | Apache running — main attack vector |

* Port 80 will likely contain the WordPress site.
* No additional ports found in typical scans.

---

📂 Proceed to [`enumeration.md`](./enumeration.md) to perform web and WordPress enumeration on the HTTP service.
