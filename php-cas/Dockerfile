FROM centos:centos7

MAINTAINER Unicon, Inc.

RUN yum -y update \
    && yum -y install httpd mod_ssl php php-pear php-xml php-pdo wget \
    && yum -y clean all

RUN pear install https://developer.jasig.org/cas-clients/php/current.tgz

COPY httpd-foreground /usr/local/bin/
COPY etc-httpd/ /etc/httpd/
COPY var-www-html/ /var/www/html/

RUN chmod +x /usr/local/bin/httpd-foreground

EXPOSE 80 443

CMD ["httpd-foreground"]