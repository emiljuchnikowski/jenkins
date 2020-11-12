FROM jenkins/jenkins:lts

ARG docker_version=19.03.6
ARG docker_tarball=https://download.docker.com/linux/static/stable/x86_64/docker-$docker_version.tgz

LABEL com.docker.version=$docker_version

USER root

# Install base packages
RUN apt-get update && apt-get install build-essential -y

RUN cd /usr/local/bin && \
    curl -s $docker_tarball | tar xz docker/docker --strip-components=1

USER jenkins
COPY init.groovy.d/plugins.groovy \
    /usr/share/jenkins/ref/init.groovy.d/plugins.groovy
