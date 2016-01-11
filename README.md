# docker-devops-stack
DevOps infrastructure stack with docker-compose (Jenkins, Selenium Grid with video recording, Weblogic admin server 10.3.6, Dind jenkins on-demand slaves, Sonar and Nexus)

## ./.env file to be created

Manually set DOCKER_HOST_IP before running docker-compose up
DOCKER_HOST_IP : Docker Host Ip to be passed to jenkins instance in order for on demand slaves to be able to contact Docker Host.

A try for jenkins user env vars to be used in credentials
JENKINS_PUBLIC_WEBHOOK_URL
JENKINS_GITHUB_CREDENTIAL_ID
JENKINS_GITHUB_CREDENTIAL_DESCRIPTION
JENKINS_GITHUB_CREDENTIAL_SECRET

## Linked repositories
**https://github.com/whren/weblogic-maven-example/** : Sample application source code used for weblogic deployment test case

**https://github.com/whren/Selenium-Maven-Template/** : Sample Selenium source code used for selenium test case

## To be built Containers
### Jenkins master
**./jenkins** (port 8080) : Jenkins master container (to be built with Dockerfile)

### Jenkins slave
**./dind-jenkins-slave** : Slave container currently used by all active jobs (to be built with Dockerfile)

### Nexus

**./nexus** (port 8081) : Nexus container (to be built with Dockerfile)

### Sonar

**./sonar** (Http port 9000, H2 Database port 9092) : Sonar container (to be built with Dockerfile)


## Other containers borrowed from docker hub
**gibaholms/weblogic-base-domain:10.3.6** (port 7001) : On demand Weblogic admin server 10.3.6, used by jenkins jobs to build dependencies, deploy and run web tests

**elgalu/selenium** (port 4444) : On demand Selenium grid (hub and node) with video recording/vnc/novnc capabilities, used by jenkins to run web tests. Videos are archived at the end of test build


## Containers currently not stable in the infra
### Hubot

**./hubot** : Hubot container
**./hubot-cfg** : Hubot config container

### Attempt to make a transparent proxy of others containers

**./iptables_docker** : Iptables container
**./squid** : Squid container
