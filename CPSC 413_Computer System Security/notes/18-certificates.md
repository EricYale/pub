# Certificates
- A certificate proves the TLS public key of a website actually belongs to the website
- Otherwise, an attacker could intercept the connection and pretend to be the website
- Certificates are signed by a Certificate Authority (CA)
    - CAs are responsible for certifying (signing) public keys
    - Browsers are pre-loaded with a list of trusted CAs
- Chain of trust: CAs can sign certificates for intermediate CAs
