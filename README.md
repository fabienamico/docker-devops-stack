# docker-devops-stack
DevOps infrastructure stack with docker-compose (Jenkins, Selenium Grid with video recording, Weblogic admin server 10.3.6, Dind jenkins on-demand slaves)

## Linked repositories
**https://github.com/whren/weblogic-maven-example/** : Sample application source code used for weblogic deployment test case

**https://github.com/whren/Selenium-Maven-Template/** : Sample Selenium source code used for selenium test case

## Jenkins master
**jenkins-sudo** (port 8080) : Jenkins master container (to be build with Dockerfile)

## Jenkins slave
**dind-jenkins-slave-sudo** : Slave container currently used by all active jobs (to be build with Dockerfile)

**headless_selenium_jenkins_slave** : Headless selenium jenkins slave, referenced in jenkins configuration, not used currently (to be build with Dockerfile)

**weblogic-base-domain-slave** : Weblogic admin server jenkins slave, referenced in jenkins configuration, not used currently (to be build with Dockerfile)

**evarga/jenkins-slave** : Base jenkins slave, referenced in jenkins configuration, not used currently (to be build with Dockerfile)

## Other containers
**gibaholms/weblogic-base-domain:10.3.6** (port 7001) : On demand Weblogic admin server 10.3.6, used by jenkins jobs to build dependencies, deploy and run web tests

**elgalu/selenium** (port 4444) : On demand Selenium grid (hub and node) with video recording/vnc/novnc capabilities, used by jenkins to run web tests. Videos are archived at the end of test build
