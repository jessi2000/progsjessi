# Camo SSRF Testing v71 - Exotic Protocol and Cache Tests

## NEW: Advanced Protocol Scheme Tests
| Test | Endpoint | Purpose |
|------|----------|--------|
| gopher:// | ![](http://164.90.187.218:9999/gophertest) | Test gopher protocol for Redis SSRF |
| dict:// | ![](http://164.90.187.218:9999/dicttest) | Test dict protocol to Memcached |
| PHP filter | ![](http://164.90.187.218:9999/phpfilter) | Test PHP stream wrappers |
| data: URI | ![](http://164.90.187.218:9999/datauri) | Test redirect to data: URI |
| HTTP/0.9 | ![](http://164.90.187.218:9999/http09) | Test HTTP/0.9 style response |
| Long chain | ![](http://164.90.187.218:9999/longchain?count=0) | Test 10-hop redirect chain to IMDS |
| Unicode host | ![](http://164.90.187.218:9999/unicodehost) | Test IDN homograph attack |

## Cache Key Manipulation Tests
| Test | Endpoint | Purpose |
|------|----------|--------|
| Cache key normal | ![](http://164.90.187.218:9999/cachekey) | Normal cache key |
| Cache key admin | ![](http://164.90.187.218:9999/cachekey?admin=true) | Cache key with query param |

## Previous Tests Still Active:
![SSRF AWS](http://164.90.187.218:9999/aws)
![OOB](http://164.90.187.218:9999/oob)
![SVG OOB](http://164.90.187.218:9999/svgoob)
![TrueDNS](http://164.90.187.218:9999/truedns)
![1ums](http://164.90.187.218:9999/1ums)
![r3dir](http://164.90.187.218:9999/r3dir)
