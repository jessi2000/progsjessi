# SSRF v9 - Fresh Webhook - Hostname & Edge Cases

## Basic Canary

![canary](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/v9-canary.gif)

## Hostname with Encoded Dot

![h1](https://webhook%2esite/d498db94-9ba8-4b98-8192-09af3fe2cbb4/h1-encoded-dot.gif)

## Fullwidth Characters

![fw1](https://webhook．site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/fw1-fullwidth.gif)

## Fragment Tricks

![frag1](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/frag1#@169.254.169.254.gif)

![frag2](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/frag2%23internal.gif)

## Port Variations

![port80](https://webhook.site:80/d498db94-9ba8-4b98-8192-09af3fe2cbb4/port80.gif)

![port443](https://webhook.site:443/d498db94-9ba8-4b98-8192-09af3fe2cbb4/port443.gif)

![port8080](https://webhook.site:8080/d498db94-9ba8-4b98-8192-09af3fe2cbb4/port8080.gif)

## Whitespace Chars

![tab](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/ws-tab%09test.gif)

![space](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/ws-space%20test.gif)

## Control Characters

![null](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/ctrl-null%00test.gif)

![bell](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/ctrl-bell%07test.gif)

![backspace](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/ctrl-bs%08test.gif)

![formfeed](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/ctrl-ff%0ctest.gif)

## Unicode Normalization

![uni1](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/uni-ℍost.gif)

![uni2](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/uni-ｈost.gif)

## Double Encoding

![de1](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/de-%252e%252e.gif)

![de2](https://webhook.site/d498db94-9ba8-4b98-8192-09af3fe2cbb4/de-%25%30d%25%30a.gif)

## DNS Canary v9

![dns1](https://v9-fresh.d498db94-9ba8-4b98-8192-09af3fe2cbb4.dnshook.site/dns1.gif)

---

*v9: Fresh webhook d498db94-9ba8-4b98-8192-09af3fe2cbb4*
