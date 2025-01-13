
# Authentication

## Authentication Factors
- **What you know**: password, security questions, pattern lock  
- **What you have**: ID card, hardware token, phone  
- **Who you are**: biometrics  
- **Where you are**: IP address, GPS  
- **How you behave**: gait detection, anomaly tracking

## Passwords

- Passwords must not be stored in plaintext; instead, they must go through a one-way hash function  
  - Hash function should change no matter how small the difference  
  - Hash function should not be able to be undone  
  - It should be hard to guess collisions  
- Passwords should be salted to prevent attackers from knowing multiple users use the same password

### Password Policies

- Password policies enforce better passwords, but they also reduce the space of possible passwords that attackers need to try  
- Results in frustrated users and less security—learning and forgetting passwords

## Rolling Codes

- Garage doors  
- MITM attack

## One Time Passwords

### On-demand

- Client (website, car key, etc) asks for a one-time random value  
- Service (server, car, etc) sends one-time random value  
- Client performs a mathematical function on the value, and transforms it into a   
- OTP  
- Service checks OTP against same algorithm performed on-service, authenticates if they match

- Can be attacked with a Man-In-The-Middle attack  
  - Attacker asks for random value  
  - Attacker sends random value to client, client sends back authenticated code  
  - Attacker blocks the code from reaching the server; saves it for later use

### Time-based

- A secret is shared between devices with synchronized clocks  
- Both devices generate OTPs based on current time  
- When user enters the OTP from the device (Google Authenticator, etc), the server checks against the current OTP it calculated

### Asymmetric (Physical Security Key)

- Setup: user’s device creates a key pair for each service, sends the public key to the server  
- Upon authentication challenge, the device signs the challenge data with the private key  
- Server verifies the signature with the public keys
