# Clickjacking

- A malicious site could put clever HTML/CSS overlayed above an iframe
- The user thinks they're clicking on the visible button, but they're actually clicking on the invisible iframe

## Preventing clickjacking
- There used to be a header called `X-Frame-Options` that disallows putting your website in an iframe
- Nowadays, you can use `Content-Security-Policy` with the `frame-ancestors` directive
    - `frame-ancestors 'none'` disallows all iframes
    - `frame-ancestors 'self'` allows iframes from the same origin
    - `frame-ancestors example.com` allows iframes from `example.com`
