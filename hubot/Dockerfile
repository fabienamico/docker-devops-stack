# DOCKER-VERSION	1.8.2

FROM iojs:latest
MAINTAINER Tanguy de Lignières, whren@free.fr

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# Env
ENV PHANTOMJS_VERSION 1.9.8

RUN npm config delete proxy
RUN npm config delete http_proxy
RUN npm config delete https_proxy

COPY package.json /usr/src/app/
RUN npm install
COPY . /usr/src/app

# Install phantomJS Commands
RUN apt-get update && \
 apt-get upgrade -y && \
 apt-get install -y vim git wget libfreetype6 libfontconfig bzip2 && \
 mkdir -p /srv/var && \
 wget -q --no-check-certificate -O /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 && \
 tar -xjf /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 -C /tmp && \
 rm -f /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 && \
 mv /tmp/phantomjs-$PHANTOMJS_VERSION-linux-x86_64/ /srv/var/phantomjs && \
 ln -s /srv/var/phantomjs/bin/phantomjs /usr/bin/phantomjs && \
 apt-get autoremove -y && \
 apt-get clean all

#  git clone https://github.com/n1k0/casperjs.git /srv/var/casperjs && \
# ln -s /srv/var/casperjs/bin/casperjs /usr/bin/casperjs && \


RUN ["chmod", "+x", "/usr/src/app/bin/hubot"]

CMD [ "npm", "start" ]