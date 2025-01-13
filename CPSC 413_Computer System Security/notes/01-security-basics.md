
# Basics of Security

**What does security ensure?**

- Confidentiality: only privileged users should be able to access information  
- Integrity: only privileged users should be able to modify information  
- Availability: authorized users should be able to use a service normally

**What can a security mechanism do?**

- Prevent an attack  
- Detect an attack  
- Recover from an attack

## Trust

### Encryption

- **Symmetric key cryptography**: secret key  
- **Asymmetric key cryptography**: public/private key  
  - **Certificates**: you can verify that someone willingly signed a message

### Central Authority

- Hierarchy of trust, leading to a central authority that everyone trusts

### Distributed Trust Model

- Web of trust  
- Start by directly verifying some people  
- Place trust in people they have trusted, with trust level decreasing across each edge  
- Some parties can be trusted more than others
