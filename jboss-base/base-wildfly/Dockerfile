FROM erikyami/base-jdk:8
MAINTAINER Erik Silva <erikyami@gmail.com>

# Set the working directory to jboss' user home directory
WORKDIR /srv/jboss


# Install packages necessary to run EAP
RUN yum update -y && yum -y install xmlstarlet saxon augeas bsdtar unzip && \
    yum clean all && rm -rf /var/cache/yum && \
    # Create a user and group used to launch processes
    mkdir -p /srv/jboss && \
    groupadd -r jboss -g 1000 && \
    useradd -u 1000 -r -g jboss -d /srv/jboss -s /sbin/nologin -c "Jboss user" jboss && \
    chmod 755 /srv/jboss


# Set the working directory to jboss' user home directory
WORKDIR /srv/jboss

#set the WILDFLY_VERSION env variable
ENV WILDFLY_VERSION 8.2.1.Final
ENV WILDFLY_SHA1 77161d682005f26acb9d2df5548c8623ba3a4905
ENV JBOSS_HOME /srv/jboss/wildfly

USER root

# Add the WildFly distribution to /opt, and make wildfly the owner of the extracted tar content
# Make sure the distribution is available from a well-known place
RUN cd $HOME \
    && curl -O https://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.tar.gz \
    && sha1sum wildfly-$WILDFLY_VERSION.tar.gz | grep $WILDFLY_SHA1 \
    && tar xf wildfly-$WILDFLY_VERSION.tar.gz \
    && mv $HOME/wildfly-$WILDFLY_VERSION $JBOSS_HOME \
    && rm wildfly-$WILDFLY_VERSION.tar.gz \
    && chown -R jboss. ${JBOSS_HOME} \
    && chmod -R g+rw ${JBOSS_HOME}

# Ensure signals are forwarded to the JVM process correctly for graceful shutdown
ENV LAUNCH_JBOSS_IN_BACKGROUND true

USER jboss

# Expose the ports we're interested in
EXPOSE 8080

# Set the default command to run on boot
# This will boot WildFly in the standalone mode and bind to all interface
CMD ["/srv/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0"]





# Set the working directory to jboss' user home directory
WORKDIR /srv/jboss

# Specify the user which should be used to execute all commands below
USER jboss

