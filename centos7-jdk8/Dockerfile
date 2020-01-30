FROM centos

LABEL maintainer="chenquan@osai.club"

ENV JAVA_VERSION="1.8.0_212" JAVA_HOME="/usr/local/src/jdk${JAVA_VERSION}" PATH="${PATH}:${JAVA_HOME}/bin"

RUN  mkdir -p /usr/local/src && yum install -y wget \
  && wget https://github.com/chenquan/oracle-jdk-download/releases/download/8u212-b10/jdk-8u212-linux-x64.tar.gz \
  && tar -xzf jdk-8u212-linux-x64.tar.gz && mv jdk${JAVA_VERSION} /usr/local/src/ && rm -f jdk-8u212-linux-x64.tar.gz
