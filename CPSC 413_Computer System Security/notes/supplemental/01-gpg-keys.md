# GPG Key Signing Process

1. Import a key into keyring (only if the person is trusted!)

```bash
gpg --import keyfile.asc
```

2. Verify it’s been imported and has the correct Username

```bash
gpg --list-keys
```

3. Verify it’s been signed by CPSC413

```bash
gpg --check-sigs "Their Name"
```

4. Sign key

```bash
gpg --sign-key "Their Name"
```

5. Verify your signature has been added 

```bash
gpg --check-sigs "Their Name"
```

6. Export the signed key and send back to them

```bash
gpg --export --armor --output signed_by_me.asc "Their Name"
```
