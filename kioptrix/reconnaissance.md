🔍 Reconnaissance – Kioptrix Level 1

This phase focuses on identifying the target VM on the network, discovering open ports, and collecting basic service information.

---

## 🌐 1. Identify Target IP Address

Assuming your host and VM are on the same subnet using NAT or bridged mode.

### 🔎 Using `netdiscover`
```bash
sudo netdiscover -r 192.168.1.0/24
````

✅ Example Output:

```
192.168.1.110   00:0C:29:AA:BB:CC   1   60   VMware, Inc.
```

> We'll use `192.168.1.110` as the Kioptrix VM IP address.

---

## 🔬 2. Run Initial Nmap Scan

Use a basic script and version scan:

```bash
nmap -sC -sV -oN nmap-basic.txt 192.168.1.110
```

✅ Output (example):

```
PORT     STATE SERVICE     VERSION
22/tcp   open  ssh         OpenSSH 2.9p2 (FreeBSD)
80/tcp   open  http        Apache httpd 1.3.20 (Unix)
111/tcp  open  rpcbind     2 (RPC #100000)
```

---

## 🚪 3. Full Port Scan

```bash
nmap -p- -T4 -oN nmap-full.txt 192.168.1.110
```

This reveals all TCP ports. Pay attention to lesser-known open services like NFS or RPC.

---

## 🖥️ 4. OS Detection & Traceroute

```bash
nmap -O -T4 192.168.1.110
nmap --traceroute 192.168.1.110
```

This gives you:

* Operating System guess (usually FreeBSD)
* Network topology

---

## 📑 Sample Nmap Summary

| Port | Service | Version Info             |
| ---- | ------- | ------------------------ |
| 22   | SSH     | OpenSSH 2.9p2 on FreeBSD |
| 80   | HTTP    | Apache 1.3.20 on Unix    |
| 111  | RPCBind | Likely used by NFS       |

---

## 🧠 Observations

* SSH may be brute-forceable if weak credentials are in use.
* Apache 1.3.20 is **very old**, likely vulnerable to multiple web-based exploits.
* RPC on port 111 might be exploitable or provide useful info (e.g., NFS shares).

---

📂 Proceed to [`enumeration.md`](./enumeration.md) to investigate these services in depth.
