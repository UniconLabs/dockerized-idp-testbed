FROM unicon/shibboleth-idp:3.2.0

MAINTAINER Unicon, Inc.

COPY shibboleth-idp/ /opt/shibboleth-idp/
COPY run-jetty.sh /usr/local/bin/

RUN chmod 750 /usr/local/bin/run-jetty.sh