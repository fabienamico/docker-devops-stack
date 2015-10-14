FROM evarga/jenkins-slave:latest

ENV DEBIAN_FRONTEND noninteractive
ENV DEBCONF_NONINTERACTIVE_SEEN true

#===================
# Timezone settings
# Possible alternative: https://github.com/docker/docker/issues/3359#issuecomment-32150214
#===================
ENV TZ "Europe/Paris"
RUN echo "Europe/Paris" | sudo tee /etc/timezone \
  && dpkg-reconfigure --frontend noninteractive tzdata

#==============
# Xvfb, firefox, maven, git
#==============
RUN apt-get update -qqy \
  && apt-get -qqy install \
    xvfb firefox maven git \
  && rm -rf /var/lib/apt/lists/*

#============================
# Some configuration options, same size as MacBook display
#============================
ENV SCREEN_WIDTH 1024
ENV SCREEN_HEIGHT 768
ENV SCREEN_DEPTH 24
ENV DISPLAY :99.0

#COPY id_rsa /home/jenkins/.ssh/
#COPY id_rsa.pub /home/jenkins/.ssh/
#RUN chown jenkins /home/jenkins/.ssh/
#RUN chmod 600 /home/jenkins/.ssh/id_rsa
#USER jenkins
#RUN ssh-keyscan qeconfig.wp.fsi >> /home/jenkins/.ssh/known_hosts
#RUN chmod 600 /home/jenkins/.ssh/id_rsa.pub
#RUN chmod 600 /home/jenkins/.ssh/known_hosts
USER root