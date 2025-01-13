# Network Encryption

## Public Key Cryptography
- Public key and private key model
- Agent can sign messages with private key, others with their public key can verify they wrote it
- Agent can decrypt messages encrypted with their public key with their private key

## TLS Handshake
1. Client hello: client announces its version, supported ciphers, and a random number (in plaintext)
2. Server hello: server responds with its version, chosen cipher, RSA/Diffie-Hellman certificate, and a random number (in plaintext)
3. Client key exchange: client generates a pub/priv keypair, and sends the private key encrypted with the server's public key
4. Client ChangeCipherSpec finished: client generates a symmetric key, sends an encrypted record of all messages so far
5. Server ChangeCipherSpec finished: server generates a symmetric key (which should match the client's); decrypts the encrypted record and verifies everything matches

## Issues with HTTPS
- UI confusion: users don't understand when a site is secure
- Users don't understand that HTTPS ≠ trusted

### SSL Stripping
- User types `http` as protocol, attacker intercepts before server can redirect to `https`
- Attacker acts as MITM, transforming users' HTTP requests to attacker-generated HTTPS requests
- HSTS can prevent this; specifies that the site should only be accessed over HTTPS
    - Browser can include a pre-loaded HSTS list in their browser binary
    - You can request this at `https://hstspreload.org`

### Mixing of HTTP and HTTPS
- Page can be served over HTTPS but contain HTTP dependencies
