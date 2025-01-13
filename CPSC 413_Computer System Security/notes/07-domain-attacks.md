# Domain Attacks

## Phishing Domain Names
- Malicious actors can reserve variations on trusted domains to trick users
    - Ex. combosquatting, typosquatting, bitsquatting, homograph attacks

## Fast-Fluxing
- A botnet can be used so there are multiple IPs hosting the same malicious site (**fast-fluxing**)
- The DNS records are constantly updated to point to different IPs
- **Double-fast fluxing**: the name server IP is also constantly changing

## Domain Generation Algorithm
- Instead of using a static IP as a Command and Control server in a botnet, a **domain generation algorithm (DGA)** can be used (since IPs can be taken down)
- The algorithm deterministically generates domain names based on timestamp
