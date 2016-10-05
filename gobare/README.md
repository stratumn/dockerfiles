# stratumn/gobare

A tiny Docker image designed to run binaries **compiled** from Golang.
It doesn't include the Golang toolkit, so the binaries have to be compiled
externally.

It starts from `scratch`, so even basic commands are unavailable. If you
need basic commands, have a look at `stratumn/gobase`, which starts from
`busybox:musl`.

It adds public SSL certificates from Mozilla so that Golang binaries can
use them to make requests to webpages, APIs, etc...

## Typical usage

```Dockerfile
FROM stratumn/gobare:latest

COPY my-binary /usr/local/bin/

CMD ["my-binary"]
```
