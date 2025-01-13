# Web Basics

## URLs

```
scheme:[//[username:password@]hostname[:port]]/path/to/resource[?query_string][#fragment]
```

- Scheme: which protocol to use
- Hostname: IP address or domain name
- Path: required path to a resource
- Query string: optional parameters
- Fragment: not sent the the server; usually used to scroll to a specific part of a page

### Open Redirect Vulnerability
- User-specified redirection, i.e. after an auth wall, to a URL specified by a query param
- Attacker could redirect to a malicious site, and use the trusted site's domain to hide the redirect

## DNS
- Decentralized—no single database
- Domain name owner may change records independently
- Hierarchical—split into zones under root zone
- 13 root name servers
    - A through M, accessible via `<letter>.root-servers.net`
    - 1000s of physical servers, using anycast networking

**Steps to resolve a query**
1. Router sends device DHCP info, with the IP of the main DNS server
2. Client sends a request to the stub resolver; stub resolver asks the recursive resolver
3. Recursive resolver iteratively resolves the query

### UDP Spoofing
- DNS runs over UDP, which is connectionless, which means it's easy to spoof
- You can spoof the source of the request, and the server will respond to the spoofed IP
- This means you can DoS a target

### Cache Poisoning
- Spoof UDP packets to "come from" real nameserver by repeatedly guessing port number and request ID
- Inject fake answer before the nameserver responds

## Domain Ecosystem
- **ICANN**: Manages the root zone, governs DNS policy, oversees TLDs, accredits registries/registrars
- **Registry**: manages TLDs, e.g. `.com` (Verisign)
- **Registrar**: sells domain names (Godaddy)
- **Registrant**: owner of the domain (web hosting providers)
