FROM centos:centos7 as stage

RUN yum -y update \
    && yum -y install ant doxygen git php-pear \
    && yum -y clean all

FROM centos:centos7

MAINTAINER Unicon, Inc.

RUN yum -y update \
    && yum -y install httpd mod_ssl php php-pear php-xml php-pdo wget \
    && yum -y clean all

RUN wget https://github.com/apereo/phpCAS/releases/download/1.3.8/CAS-1.3.8.tgz \
 && tar zxvpf CAS-1.3.8.tgz

RUN pear install CAS-1.3.8.tgz

COPY httpd-foreground /usr/local/bin/
COPY etc-httpd/ /etc/httpd/
COPY var-www-html/ /var/www/html/

RUN chmod +x /usr/local/bin/httpd-foreground

EXPOSE 80 443

CMD ["httpd-foreground"]
