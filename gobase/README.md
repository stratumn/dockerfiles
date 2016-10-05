# stratumn/gobase

A very small Docker image designed to run binaries **compiled** from Golang.
It doesn't include the Golang toolkit, so the binaries have to be compiled
externally.

It starts from `busybox:musl`, so basic commands are available, and it only
adds about 1.2 MB uncompressed. If you don't need basic commands, have a look
at `stratumn/gobare`.

It adds public SSL certificates from Mozilla so that Golang binaries can
use them to make requests to webpages, APIs, etc...

## Typical usage

```Dockerfile
FROM stratumn/gobase:latest

COPY my-binary /usr/local/bin/

CMD ["my-binary"]
```
