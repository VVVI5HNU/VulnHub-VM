🚩 Flags – Mr. Robot

This file documents all the flags captured throughout the exploitation process, confirming full compromise of the system.

---

## 📍 Flag 1 of 3

**Location**: `/robots.txt`  
**How**: Discovered via directory brute-force and inspection of the robots file.

```text
Key 1: 073403c8a58a1f80d943455fb30724b9
````

---

## 📍 Flag 2 of 3

**Location**: `/home/robot/key-2-of-3.txt`
**How**: Cracked MD5 hash from `password.raw-md5`, logged in as `robot`.

```text
Key 2: 822c73956184f694993bede3eb39f959
```

---

## 📍 Flag 3 of 3

**Location**: `/root/key-3-of-3.txt`
**How**: Used interactive mode of `nmap` to gain a root shell.

```text
Key 3: 04787ddef27c3dee1ee161b21670b4e4
```

---

## 🏁 Summary

| Flag Number | Location       | Method                        |
| ----------- | -------------- | ----------------------------- |
| Flag 1      | `/robots.txt`  | Web enumeration               |
| Flag 2      | `/home/robot/` | Cracked MD5 → `su robot`      |
| Flag 3      | `/root/`       | Nmap interactive shell → root |

---

🎉 Congratulations! All 3 flags have been captured and full system access was achieved.
