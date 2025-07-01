🚩 Flags – Metasploitable

This section captures the key proof-of-access indicators such as user-level and root-level flags collected during exploitation and privilege escalation.

---

## 👤 User Access Achieved

- ✅ Gained shell via **Telnet** using credentials:
  - `msfadmin:msfadmin`
- ✅ Also accessed via **FTP backdoor** and **Tomcat WAR reverse shell**

---

## 🧾 User Flag (Optional)

Metasploitable doesn't contain a standard CTF-style user flag, but confirmation of access was demonstrated with:

```bash
whoami
# Output: msfadmin
````

---

## 👑 Root Access Achieved

Successfully escalated privileges using a local kernel exploit (`2.6.24`) after enumeration with LinEnum/LinPEAS.

```bash
whoami
# Output: root
```

✅ Created a root proof file:

```bash
echo "Rooted Metasploitable!" > /root/pwned.txt
```

---

## 🏁 Summary

| Access Level | Method Used                      | Success |
| ------------ | -------------------------------- | ------- |
| User         | Telnet (`msfadmin:msfadmin`)     | ✅       |
| User         | Tomcat WAR reverse shell         | ✅       |
| Root         | Kernel exploit (e.g., Dirty COW) | ✅       |

---

🎉 Congratulations! The Metasploitable VM has been fully compromised and rooted successfully.
