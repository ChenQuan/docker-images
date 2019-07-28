FROM centos

LABEL maintainer="chenquan@osai.club"

ENV JAVA_VERSION="1.8.0_141"

ENV JAVA_HOME="/usr/local/src/jdk${JAVA_VERSION}"

ENV PATH="${PATH}:${JAVA_HOME}/bin"

RUN  mkdir -p /usr/local/src && yum install -y wget \
  && wget --no-cookies --no-check-certificate --header \
   "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" \
   "http://download.oracle.com/otn-pub/java/jdk/8u141-b15/336fa29ff2bb4ef291e347e091f7f4a7/jdk-8u141-linux-x64.tar.gz" \
  && tar -xzf jdk-8u141-linux-x64.tar.gz && mv jdk${JAVA_VERSION} /usr/local/src/
