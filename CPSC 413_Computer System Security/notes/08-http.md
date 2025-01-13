# HTTP

## Version History

**HTTP 0.9**
- Original version invented by Tim Berners-Lee in 1989
- Simple protocol: client sends a single-line request, server responds with a text file

**HTTP 1.0**
- Added support for headers, compression, and error handling

**HTTP 1.1**
- Added ability to send multiple requests/responses over the same TCP connection

**HTTP 2.0**
- Multiplexing: multiple requests can be sent at the same time
- Server push: server can send resources (like CSS or JS) before the client requests them
    - Removed from Chrome in 2022 due to low adoption and marginal performance improvements

**HTTP 3.0**
- Standardized in 2022
- TCP replaced with QUIC
- Better at handling "head-of-line" response blocking (i.e. the initial HTML file must complete before dependencies can be loaded)
- Forces use of encryption
