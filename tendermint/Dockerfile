FROM golang:1.6

ENV USER tmuser
ENV DATA_ROOT /data/tendermint
ENV TMREPO "github.com/tendermint/tendermint"
ENV TMVERSION "v0.8.0"

# Set user right away for determinism
RUN groupadd -r $USER \
  && useradd -r -s /bin/false -g $USER $USER

# Create home directory for USER
# Needed for nodejs/nom
RUN mkdir -p /home/$USER \
  && chown -R $USER:$USER /home/$USER

# Create directory for persistence and give our user ownership
RUN mkdir -p $DATA_ROOT \
  && chown -R $USER:$USER $DATA_ROOT

# Set the env variables to non-interactive
ENV DEBIAN_FRONTEND noninteractive
ENV DEBIAN_PRIORITY critical
ENV DEBCONF_NOWARNINGS yes
ENV TERM linux
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

# Grab deps (git)
RUN apt-get update && \
  apt-get install -y --no-install-recommends \
    git && \
  rm -rf /var/lib/apt/lists/*

# Grab deps (node)
RUN curl -sL https://deb.nodesource.com/setup_5.x | bash -
RUN apt-get update && \
  apt-get install -y --no-install-recommends \
    nodejs && \
  rm -rf /var/lib/apt/lists/*


USER $USER
ENV TMROOT $DATA_ROOT

RUN mkdir -p $GOPATH/src/$TMREPO
WORKDIR $GOPATH/src/$TMREPO
RUN git clone https://$TMREPO.git . \
    && git fetch \
    && git reset --hard $TMVERSION \
    && go get -d $TMREPO/cmd/tendermint \
    && make \
    && tendermint init

# Persist data
WORKDIR $DATA_ROOT
VOLUME $DATA_ROOT

EXPOSE 46656
EXPOSE 46657
CMD ["tendermint", "node"]
