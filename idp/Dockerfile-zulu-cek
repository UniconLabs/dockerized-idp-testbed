FROM unicon/shibboleth-idp:latest

MAINTAINER Unicon, Inc.

COPY shibboleth-idp/ /opt/shibboleth-idp/
COPY shib-jetty-base/ /opt/shib-jetty-base/


#Testing JCE code as well (from base image's readme)
RUN yum -y update \
    && yum -y install unzip

RUN wget http://cdn.azul.com/zcek/bin/ZuluJCEPolicies.zip \
    && echo "8021a28b8cac41b44f1421fd210a0a0822fcaf88d62d2e70a35b2ff628a8675a  ZuluJCEPolicies.zip" | sha256sum -c - \
    && unzip -oj ZuluJCEPolicies.zip ZuluJCEPolicies/local_policy.jar -d /opt/jre-home/lib/security/ \
    && unzip -oj ZuluJCEPolicies.zip ZuluJCEPolicies/US_export_policy.jar -d /opt/jre-home/lib/security/ \
    && rm ZuluJCEPolicies.zip \
    && chmod -R 640 /opt/jre-home/lib/security/ \
    && chown -R root:jetty /opt/jre-home/lib/security/   
