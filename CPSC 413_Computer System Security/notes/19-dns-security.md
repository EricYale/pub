# DNS Security

## DNSSEC
- DNSSEC is a way to cryptographically sign DNS records
- There is no encryption—DNSSEC offers integrity, but not confidentiality
- Chain of trust
    - When registering a domain, you give the registrar a DS (Delegation Signee) record; this record is included in the zonefile for the TLD
    - Root key is signed at the wizard ceremony

## DNS over HTTPS

## DNS over TLS
