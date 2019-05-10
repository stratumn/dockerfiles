FROM pcisupport/ci-awscli-java-mvn-sonarscanner

MAINTAINER Mourad BEJI <mourad@stratumn.com>


RUN sudo wget https://dl.google.com/go/go1.12.2.linux-amd64.tar.gz
# COPY go1.12.2.linux-amd64.tar.gz go1.12.2.linux-amd64.tar.gz
RUN sudo tar -C /usr/local -xzf go1.12.2.linux-amd64.tar.gz
RUN sudo rm go1.12.2.linux-amd64.tar.gz


# Configure Go
ENV GOPATH /go
ENV PATH $PATH:/usr/local/go/bin:$GOPATH/bin

RUN sudo mkdir -p ${GOPATH}/src ${GOPATH}/bin
