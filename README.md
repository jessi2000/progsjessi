# Security Research - v29

## Protocol & Advanced Attacks

Testing protocol-level and advanced SSRF techniques.

---

### 1) Gopher Protocol

SSRF classic - gopher can craft arbitrary TCP:

![gopher](gopher://127.0.0.1:9000/_GET%20/%20HTTP/1.0%0d%0a%0d%0a)

---

### 2) Dict Protocol

Dict protocol for port scanning:

![dict](dict://127.0.0.1:6379/INFO)

---

### 3) LDAP Protocol

![ldap](ldap://127.0.0.1:389/)

---

### 4) TFTP Protocol

![tftp](tftp://127.0.0.1/test)

---

### 5) FTP Protocol

![ftp](ftp://127.0.0.1/)

---

### 6) CRLF Injection in URL

Attempt CRLF in path:

![crlf](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/test%0d%0aX-Injected:%20header%0d%0a%0d%0a/crlf.gif)

---

### 7) HTTP Request Smuggling via URL

Attempt smuggling in path:

![smuggle](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/test%20HTTP/1.1%0d%0aHost:%20127.0.0.1%0d%0a%0d%0aGET%20/smuggled.gif)

---

### 8) Connection: Keep-Alive Pipeline

![keepalive](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/keepalive.gif)

---

### 9) URL with Different Case Scheme

![HTTP-case](HTTP://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/http-case.gif)

![hTtP-case](hTtP://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/http-mixed.gif)

---

### 10) Double Slash Normalization

![doubleslash](https://webhook.site//dfe7c107-9e29-45d2-b866-cf64a684164e//doubleslash.gif)

---

### 11) URL with Backslash in Host

![backslash-host](https://webhook.site\@127.0.0.1/backslash-host.gif)

---

### 12) Tab Character in Host

![tab-host](https://webhook	.site/dfe7c107-9e29-45d2-b866-cf64a684164e/tab-host.gif)

---

### 13) Semicolon as Path Separator

![semicolon](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e;@127.0.0.1/semicolon.gif)

---

### 14) IPv4-in-IPv6 Format

![ipv4-in-ipv6](http://[::ffff:127.0.0.1]/ipv4-in-ipv6.gif)

---

### 15) Long URL Overflow Test

Extremely long path:

![longurl](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/longurl.gif)

---

### 16) URL with Username Only (No Password)

![user-only](https://user@webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/user-only.gif)

---

### 17) Percent-Encoded Scheme

![encoded-scheme](%68%74%74%70%73://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/encoded-scheme.gif)

---

### 18) Unicode Normalization (NFC vs NFD)

![nfc](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/café-nfc.gif)
![nfd](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/cafe\u0301-nfd.gif)

---

### 19) HTTP/2 Pseudo-Header Injection

![h2-inject](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/:path/h2-inject.gif)

---

### 20) URL Fragment with Query String

![fragment-query](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/test.gif?foo=bar#baz?internal=http://127.0.0.1)

---

### DNS Exfil

![dns](https://v29-dns.dfe7c107-9e29-45d2-b866-cf64a684164e.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/dfe7c107-9e29-45d2-b866-cf64a684164e/v29-canary.gif)

---

*v29 - Protocol & advanced attacks*
