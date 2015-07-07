FROM centos:7
MAINTAINER Eric Bottard; Charlie Pence

# 'snapshot' or 'release'
ENV XD_BUILD snapshot
ENV XD_VERSION 2.0.0.BUILD-SNAPSHOT

RUN groupadd -r springxd && useradd -r -g springxd springxd

RUN yum -y update && yum -y install unzip rsync java-1.7.0-openjdk-devel wget

RUN wget http://repo.spring.io/${XD_BUILD}/org/springframework/xd/spring-xd/${XD_VERSION}/spring-xd-${XD_VERSION}-dist.zip \
      -O /opt/spring-xd-${XD_VERSION}-dist.zip \
    && unzip /opt/spring-xd-${XD_VERSION}-dist.zip -d /opt/ \
    && rm /opt/spring-xd-${XD_VERSION}-dist.zip \
    && /opt/spring-xd-${XD_VERSION}/zookeeper/bin/install-zookeeper \
    && chown -R springxd:springxd /opt/spring-xd-${XD_VERSION} \
    && ln -s /opt/spring-xd-${XD_VERSION} /opt/spring-xd

USER springxd
WORKDIR /opt/spring-xd
