🚩 Flags – Kioptrix Level 1

This section documents proof of exploitation and successful privilege escalation.

---

## 👤 User Access Achieved

Access to the machine was obtained using:

- ✅ **Command Injection** via vulnerable `test.php` page
- ✅ **Apache Chunked Transfer Buffer Overflow** exploit (Metasploit)
- ✅ Reverse shell received on port `4444`

---

## 🧾 User Shell Confirmation

```bash
whoami
# Output: www-data or apache
````

---

## 👑 Root Access Achieved

Privilege escalation was successful via a FreeBSD 6.x kernel exploit (`kldload` or similar local exploit).

```bash
whoami
# Output: root
```

✅ Root shell confirmed.

---

## 🧾 Root Proof

Created root-level proof of exploitation:

```bash
echo "Rooted Kioptrix Level 1!" > /root/pwned.txt
```

✅ File successfully written and verified.

---

## 🏁 Summary

| Access Level | Method                             | Success |
| ------------ | ---------------------------------- | ------- |
| User         | Web command injection / Metasploit | ✅       |
| Root         | Kernel exploit (FreeBSD 6.x)       | ✅       |

---

🎉 Congratulations! The Kioptrix Level 1 machine has been fully compromised.
