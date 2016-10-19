FROM nodesource/xenial:6.3.1
MAINTAINER Da Vinci Studio <kontakt@davinci-studio.com>

# Update apt
RUN apt-get update

# Install apt packages
RUN apt-get install -y --no-install-recommends \
    wget \
    curl \
    ca-certificates \
    libfreetype6 \
    libfontconfig \
    bzip2 \
    rsync \
    ssh \
    git;

# Set ENV
ENV NODE_ENV dev
ENV PHANTOMJS_VERSION 1.9.8

# Commands
RUN \
  npm install -g gulp bower npm-cache yarn && \
  npm cache clean && \
  mkdir -p /srv/var && \
  wget -q --no-check-certificate -O /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 && \
  tar -xjf /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 -C /tmp && \
  rm -rf /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 && \
  mv /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/ /srv/var/phantomjs && \
  ln -s /srv/var/phantomjs/bin/phantomjs /usr/bin/phantomjs && \
  apt-get -yqq autoremove && \
  apt-get -yqq clean && \
  rm -rf /var/lib/apt/lists/* /var/cache/* /tmp/* /var/tmp/*

RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo
RUN chown -R docker:docker /opt/ /usr/local/
USER docker
