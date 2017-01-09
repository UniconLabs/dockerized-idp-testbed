FROM unicon/simplesamlphp

RUN yum -y update \
    && yum -y install php55w-ldap \
    && yum -y clean all

COPY etc-httpd /etc/httpd/
COPY var-simplesamlphp /var/simplesamlphp/
COPY var-www-html/ /var/www/html/

RUN chown apache:apache /var/simplesamlphp/log/ \
    && chown -R apache:apache /var/simplesamlphp/cert/
