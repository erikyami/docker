FROM erikyami/centos:7.7-base
MAINTAINER Erik Silva <erikyami@gmail.com>

# Install necessary packages
RUN yum update && yum -y install java-11-openjdk && yum clean all && rm -rf /var/cache/yum

# Set the JAVA_HOME variable to make it clear where Java is located
ENV JAVA_HOME /usr/lib/jvm/java
