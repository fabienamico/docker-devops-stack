FROM gibaholms/weblogic-base-domain:10.3.6

# Install a basic SSH server
USER root
RUN yum install openssh openssh-server
RUN sed -i 's|session required pam_loginuid.so|session optional pam_loginuid.so|g' /etc/pam.d/sshd
RUN mkdir -p /var/run/sshd

# Add user jenkins to the image
RUN adduser jenkins
# Set password for the jenkins user (you may want to alter this).
RUN echo "jenkins:jenkins" | chpasswd
USER oracle

# Standard SSH port
EXPOSE 22

CMD ["/usr/sbin/sshd -D && startWebLogic.sh"]
