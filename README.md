# v52: Advanced Vulnerability Testing

> Testing timing attacks, large payloads, slow responses, header leakage, and more.
> Server running on `164.90.187.218:8888` via `nip.io`.

---

## 1. Timing Attacks (Time-based SSRF)

### 2 second delay
![time2](http://164.90.187.218.nip.io:8888/timing?delay=2)

### 5 second delay
![time5](http://164.90.187.218.nip.io:8888/timing?delay=5)

---

## 2. Resource Exhaustion / DoS

### Large File (10MB)
![large](http://164.90.187.218.nip.io:8888/large)

### Slow Response (Hanging connection)
![slow](http://164.90.187.218.nip.io:8888/slow)

---

## 3. Information Leakage

### Request Headers Leakage
![headers](http://164.90.187.218.nip.io:8888/headers)

---

## 4. Redirect Chains

### Multi-step Redirect (Self-referential loop/chain)
![redir-chain](http://164.90.187.218.nip.io:8888/redirect-chain)

---

## 5. Internal Service Simulation

### Fake AWS Metadata
![aws-fake](http://164.90.187.218.nip.io:8888/aws-fake)

---

## 6. Cache Poisoning

### Cache Control Test (Long max-age)
![cache](http://164.90.187.218.nip.io:8888/cache-poison)

---

**v52** - Advanced Testing Suite
