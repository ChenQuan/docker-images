FROM chenquan97/centos7-systemctl

RUN yum install -y wget \
  && cd /etc/yum.repos.d/ \
  && wget http://mirrors.163.com/.help/CentOS6-Base-163.repo \
  && sed -i 's#$releasever#6#g' CentOS6-Base-163.repo \
  && yum clean all && yum makecache fast  && yum update -y \
  && yum install -y  gcc-c++ pcre pcre-devel zlib zlib-devel  openssl openssl-devel 

RUN wget https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.22.0.tar.gz \
  && tar -zxf git-2.22.0.tar.gz && mv git-2.22.0 /usr/local/src/git-2.22.0 \
  && yum install -y curl-devel expat-devel gettext-devel openssl-devel zlib-devel \
  && yum install -y gcc perl-ExtUtils-MakeMaker \
  && cd  /usr/local/src/git-2.22.0 && ./configure --prefix=/usr/local/git \
  $$ make && make install

RUN yum -y install java-1.8.0-openjdk-devel.x86_64 \

  && touch /etc/profile.d/java.sh \
  && echo "export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.212.b04-0.el7_6.x86_64" >> touch /etc/profile.d/java.sh  \
  && echo "export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar" >> touch /etc/profile.d/java.sh  \ 
  && echo "export PATH=$PATH:$JAVA_HOME/bin" >> touch /etc/profile.d/java.sh \
  && source /etc/profile 

RUN wget http://nginx.org/download/nginx-1.8.1.tar.gz \
  && tar -zxvf nginx-1.8.1.tar.gz && cd nginx-1.8.1 \
  && ./configure --prefix=/usr/src/nginx --with-http_stub_status_module --with-http_ssl_module \
  && make && make install \
  && cd /usr/src/nginx/sbin \
  && ./nginx -v \
  && echo "/usr/src/nginx/sbin/nginx" >> /etc/rc.local \
  && cd /usr/src/nginx/sbin && ./nginx

RUN wget https://nodejs.org/dist/v10.15.0/node-v10.15.0-linux-x64.tar.xz \
  && tar -xvf node-v10.15.0-linux-x64.tar.xz \
  && mv node-v10.15.0-linux-x64 /usr/local/node-v10.15.0 \
  && ln -s /usr/local/node-v10.15.0/bin/node /usr/local/bin/node \
  && ln -s /usr/local/node-v10.15.0/bin/npm /usr/local/bin/npm \
  && ln -s /usr/local/node-v10.15.0/bin/npx /usr/local/bin/npx \
  && node -v && npm -v && npx -v


#CMD ["/usr/sbin/init"]
#RUN  systemctl start docker && systemctl enable docker \
#  && docker -v
# CMD [ "/usr/sbin/init" ]
#RUN yum install -y yum-utils device-mapper-persistent-data lvm2 \
#  && yum-config-manager --add-repo  http://download.docker.com/linux/centos/docker-ce.repo\
#  && yum makecache fast \
#  && yum install -y  docker-ce

RUN yum install -y epel-release \
  && yum install -y python-pip 
 
RUN pip install --upgrade pip \
  && pip install docker-compose \
  && docker-compose -version

# RUN wget https://www.kernel.org/pub/software/scm/git/git-2.9.4.tar.gz \
#  && tar -zxvf git-2.9.4.tar.gz \
#  && yum install -y curl-devel expat-devel gettext-devel openssl-devel zlib-devel \
#  && yum install -y  gcc perl-ExtUtils-MakeMaker \
#  && mv git-2.9.4 /usr/local/src/git-2.9.4 \ 
#  && cd /usr/local/src/git-2.9.4 \
#  && ./configure --prefix=/usr/local/git \
#  && make && make install \
#  && ln -s /usr/local/git/bin/* /usr/local/bin/ \
#  && git --version && ssh-keygen -t rsa -C "quan.chen@hand-china.com" 

RUN wget http://mirror.bit.edu.cn/apache/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz \
  && tar -zxvf apache-maven-3.3.9-bin.tar.gz \
  && mv apache-maven-3.3.9 /usr/local/maven3 \
  && touch /etc/profile.d/mvn.sh \
  && echo "export MAVEN_HOME=/usr/local/maven3" >> /etc/profile.d/mvn.sh \
  && echo "export PATH=$MAVEN_HOME/bin:$PATH" >> /etc/profile.d/mvn.sh \
  && source /etc/profile
## docker image
#RUN systemctl start docker

#RUN docker pull redis \
#  && docker pull registry.cn-hangzhou.aliyuncs.com/choerodon-tools/mysql:5.7.17 \
#  && docker pull minio/minio:RELEASE.2018-05-25T19-49-13Z \
#  && docker pull jenkins \
CMD ["/usr/sbin/init"]
