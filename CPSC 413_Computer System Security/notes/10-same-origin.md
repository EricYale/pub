# Same Origin Policy
- Same-Origin Policy is a basic access control policy implemented in web browsers.
- Active on three actions
    - Script access to other document in same browser (iframes, other tabs)
    - Script access to local state (cookies, local storage)
    - HTTP requests to other hosts (fetch, XMLHttpRequest)
- Same-Origin Policy only allows if origins match (protocol, host, port: `https://example.com:80`)

## Motivation
- Example: fetch request from `evil.com` to `wellsfargo.com`
- By default, the cookies of the target domain (wellsfargo.com) would be sent along with the request
- So, the browser blocks cross-origin requests

## Ways to get around SOP
### Domain Relaxation
- A subdomain can choose to set `document.domain` to a parent domain
- If both origins set `document.domain` to the same value, they can communicate

### `window.name`
- The only property on another document's window object that you can access is `window.name`
- Old sites used a hack where they set `window.name` to communicate

### JSONP
- "JSON with padding"
- Since resources can be included from remote origins, you can include a `<script>` tag with a URL that returns JSONP
- The JSONP file is a script that does nothing except set a variable to some data

**Problems with JSONP**
- You are fully trusting the remote website
- No error management if the JSONP request is not OK
- The only security measure is Referer checking

### CORS
- Cross-Origin Resource Sharing
- CORS policy is sent by server in `Origin` header, and interpreted by the browser

#### CORS response headers
- `Access-Control-Allow-Origin`: specifies which origins are allowed to access the resource
    - `*` alows all origins, but cannot be used with credentialed requests
- `Access-Control-Allow-Credentials`: indicates whether the response can be read if credentials (e.g. cookies) were requested
- `Access-Control-Expose-Headers`: specifies which headers can be accessed by Javascript
- `Access-Control-Max-Age`: cache lifetime of a preflight request
- `Access-Control-Allow-Methods`: specifies which HTTP methods are allowed
- `Access-Control-Allow-Headers`: specifies which headers can be used in the actual request

#### Preflight requests
- For certain requests (e.g. `PUT`, `DELETE`, or requests with custom headers), the browser sends an initial `OPTIONS` request to check if the actual request is safe to send
- If the server responds with the appropriate CORS headers, the browser will proceed with the actual request
- Preflight requests have headers too
    - `Access-Control-Request-Method`: the method that will be used in the actual request
    - `Access-Control-Request-Headers`: the headers that will be sent in the actual request
    - `Origin`: the origin of the requester
