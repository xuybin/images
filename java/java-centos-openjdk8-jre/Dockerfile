FROM centos

USER root

RUN mkdir -p /deployments

# JAVA_APP_DIR is used by run-java.sh for finding the binaries
ENV JAVA_APP_DIR=/deployments \
    JAVA_MAJOR_VERSION=8

# /dev/urandom is used as random source, which is prefectly safe
# according to http://www.2uo.de/myths-about-urandom/
RUN yum install -y \
       java-1.8.0-openjdk \
    && echo "securerandom.source=file:/dev/urandom" >> /usr/lib/jvm/jre/lib/security/java.security



ENV JAVA_HOME /etc/alternatives/jre


# Add run script as /deployments/run-java.sh and make it executable
COPY ./run-java.sh /deployments/
RUN chmod 755 /deployments/run-java.sh


CMD [ "/deployments/run-java.sh" ]
