FROM pcisupport/ci-awscli-java-mvn-sonarscanner

MAINTAINER Mourad BEJI <mourad@stratumn.com>

RUN sudo mkdir -p /usr/local/var
WORKDIR /usr/local/var

RUN sudo wget https://dl.google.com/go/go1.12.2.linux-amd64.tar.gz
# COPY go1.12.2.linux-amd64.tar.gz go1.12.2.linux-amd64.tar.gz
RUN sudo tar -C . -xzf go1.12.2.linux-amd64.tar.gz
RUN sudo rm go1.12.2.linux-amd64.tar.gz


# Configure Go
ENV GOPATH /go
ENV PATH $PATH:/usr/local/var/go/bin:$GOPATH/bin

RUN sudo mkdir -p ${GOPATH}/src ${GOPATH}/bin
RUN sudo chmod -R 777 .
RUN sudo chmod -R 777 ${GOPATH}
