# Cross-Site Scripting

## Reflected Server-Side XSS
- When user-contorlled input, e.g. in a URL, is displayed on the page

## Persistent Server-Side XSS
- When a user inputs a string that's displayed to other people, e.g. Facebook post

## Preventing XSS
### Denylisting
- Block certain strings, e.g. `<script>`
- Simple replacement doesn't work: `<scr<script>ipt>`

### Allowlisting
- i.e. alphanumeric only

### Escaping/encoding
- Neutralize control characters

### Content Security Policy (CSP)
- Server sends the `Content-Security-Policy` header
- Sets a list of sources that are trusted in the client, i.e. JS, iframe, etc
    - You can control where images come from (`img-src`), where scripts come from (`script-src`), etc
    - if `script-src` is provided, inline scripts and `eval()` will be blocked

#### CSP Level 2
- You can use nonces or hashes to make inline scripts more secure
    - If the hash of the script doesn't match the provided hash, it throws an error
- Additional directives
    - `child-src` (replacement for `frame-src` in v2)
    - `base-uri`: controls whether `<base>` can be used
        - `<base>` changes the base URL for relative URLs
    - `form-action`: controls where forms can be submitted

#### CSP Level 3
- `frame-src` undeprecated, changed back from `child-src` in v3
- `worker-src`: controls where web workers can be loaded from
- `manifest-src`: controls where AppCache manifest files can be loaded from
- `strict-dynamic`: allows adding scripts programmatically (e.g. for ad loading)
    - Only allows non-"parser-inserted" methods, i.e. `appendChild` instead of `document.write`

#### CSP Reporting
- CSP can send reports to a URL when a violation occurs
- `report-uri` specifies where to send the reports

## Domain Rebinding Attack
- To get around CSP, an attacker can use a domain rebinding attack
- The attacker loads the DNS server with the correct IP address, but then quickly swaps it before the correct website makes a dependency request
- The attacker can then load a malicious script from the malicious IP, but the browser thinks it's from the same domain
- To prevent this, Chrome ignores short TTL values and keeps cache for a minimum of 1600s
