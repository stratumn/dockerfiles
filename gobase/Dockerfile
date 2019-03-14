FROM golang:1.12.0

MAINTAINER Stephan Florquin <stephan@stratumn.com>

FROM busybox:1.30.1-glibc

COPY etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --from=0 /lib/x86_64-linux-gnu/libdl-2.24.so /lib/libdl.so.2
