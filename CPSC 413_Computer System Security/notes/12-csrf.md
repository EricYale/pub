# Cross-Site Request Forgery (CSRF)
- A malicious site can make a request to a site you're logged into
- By default, the browser will send the cookies of the destination origin
- Even though the malicious site can't read the response, the request still goes through

## Ways to stop CSRF
### Nonces
- The server can include a random, unique nonce in the valid webpage, and expect that nonce with all requests

### SameSite cookie
- A cookie attribute that prevents the browser from sending cookies in a cross-site request
    - Includes clicking links—you can click a link and it's not SameSite, but you refresh and then it _is_ SameSite

- `SameSite=Strict`
    - Cookies are only sent in a first-party context
    - However, this may be frustrating. Example: click a link to a Facebook image, you have to refresh the page to view it
- `SameSite=Lax`
    - Cookies will be attached as long as the request is GET, and it results in a top-level change (no iframes or XHR)
