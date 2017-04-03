FROM unicon/shibboleth-idp:latest

MAINTAINER Unicon, Inc.

COPY shibboleth-idp/ /opt/shibboleth-idp/
COPY shib-jetty-base/ /opt/shib-jetty-base/

RUN yum -y update \
    && yum -y install unzip

#Remove OpenJDK
RUN cd /opt \
    && rm -rf zulu*/

#Install Oracle JVM
RUN java_version=8u71; \
    java_bnumber=15; \
    java_semver=1.8.0_71; \
    java_hash=429c3184b10d7af2bb5db3faf20b467566eb5bd95778f8339352c180c8ba48a1; \
    wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    http://download.oracle.com/otn-pub/java/jdk/$java_version-b$java_bnumber/server-jre-$java_version-linux-x64.tar.gz \
    && echo "$java_hash  server-jre-$java_version-linux-x64.tar.gz" | sha256sum -c - \
    && tar -zxvf server-jre-$java_version-linux-x64.tar.gz -C /opt \
    && rm server-jre-$java_version-linux-x64.tar.gz \
    && ln -sf /opt/jdk$java_semver/ /opt/jre-home
