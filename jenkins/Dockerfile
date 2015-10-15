FROM jenkins

USER root
RUN apt-get update \
      && apt-get install -y sudo \
      && rm -rf /var/lib/apt/lists/*
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

USER jenkins
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt

# Adding default Jenkins Jobs
COPY jobs/1-maven-build-weblogic-dind-job.xml /usr/share/jenkins/ref/jobs/1-maven-build-weblogic-dind-job/config.xml
COPY jobs/2-deploy-to-weblogic-dind-job.xml /usr/share/jenkins/ref/jobs/2-deploy-to-weblogic-dind-job/config.xml
COPY jobs/3-maven-tests-on-selenium-grid-dind-job.xml /usr/share/jenkins/ref/jobs/3-maven-tests-on-selenium-grid-dind-job/config.xml
COPY jobs/4-maven-sonar-dind-job.xml /usr/share/jenkins/ref/jobs/4-maven-sonar-dind-job/config.xml

############################################
# Configure Jenkins
############################################
# Jenkins settings
COPY config/config.xml /usr/share/jenkins/ref/config.xml

# Credentials
COPY config/credentials.xml /usr/share/jenkins/ref/credentials.xml
RUN mkdir -p /usr/share/jenkins/ref/secrets
COPY secrets/master.key /usr/share/jenkins/ref/secrets/master.key
COPY secrets/hudson.util.Secret /usr/share/jenkins/ref/secrets/hudson.util.Secret


# Jenkins Settings, i.e. Maven, Groovy, ...
COPY config/jenkins.model.JenkinsLocationConfiguration.xml /usr/share/jenkins/ref/jenkins.model.JenkinsLocationConfiguration.xml
COPY config/jenkins.mvn.GlobalMavenConfig.xml /usr/share/jenkins/ref/jenkins.mvn.GlobalMavenConfig.xml
COPY config/github-plugin-configuration.xml /usr/share/jenkins/ref/github-plugin-configuration.xml
COPY config/hudson.plugins.copyartifact.TriggeredBuildSelector.xml /usr/share/jenkins/ref/hudson.plugins.copyartifact.TriggeredBuildSelector.xml
COPY config/hudson.plugins.groovy.Groovy.xml /usr/share/jenkins/ref/hudson.plugins.groovy.Groovy.xml
COPY config/hudson.tasks.Maven.xml /usr/share/jenkins/ref/hudson.tasks.Maven.xml
COPY config/hudson.maven.MavenModuleSet.xml /usr/share/jenkins/ref/hudson.maven.MavenModuleSet.xml
COPY config/maven-global-settings-files.xml /usr/share/jenkins/ref/maven-global-settings-files.xml
COPY config/org.jenkins_ci.plugins.flexible_publish.FlexiblePublisher.xml /usr/share/jenkins/ref/org.jenkins_ci.plugins.flexible_publish.FlexiblePublisher.xml
COPY config/org.jenkinsci.plugins.conditionalbuildstep.singlestep.SingleConditionalBuilder.xml /usr/share/jenkins/ref/org.jenkinsci.plugins.conditionalbuildstep.singlestep.SingleConditionalBuilder.xml
COPY config/thinBackup.xml /usr/share/jenkins/ref/thinBackup.xml

# Jenkins user
RUN mkdir -p /usr/share/jenkins/ref/users/jenkins
COPY users/jenkins/config.xml /usr/share/jenkins/ref/users/jenkins/config.xml