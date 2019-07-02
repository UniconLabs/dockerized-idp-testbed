FROM centos:centos7 as stage

RUN yum -y update \
    && yum -y install ant doxygen git php-pear \
    && yum -y clean all

RUN git clone --depth=1 --branch=1.3-stable https://github.com/apereo/phpCAS.git apereo/phpCAS \
 && pear upgrade --force --alldeps \
 && cd apereo/phpCAS/utils \
 && pear install --onlyreqdeps PEAR_PackageFileManager2-beta \
 && ant dist -Ddoxygen.path=/usr/bin/doxygen -Dphp.path=/usr/bin/php

FROM centos:centos7

MAINTAINER Unicon, Inc.

RUN yum -y update \
    && yum -y install httpd mod_ssl php php-pear php-xml php-pdo wget \
    && yum -y clean all

COPY --from=stage /apereo/phpCAS/utils/dist/CAS-1.3.4.tgz /

RUN pear install CAS-1.3.4.tgz \
 && rm /CAS-1.3.4.tgz

COPY httpd-foreground /usr/local/bin/
COPY etc-httpd/ /etc/httpd/
COPY var-www-html/ /var/www/html/

RUN chmod +x /usr/local/bin/httpd-foreground

EXPOSE 80 443

CMD ["httpd-foreground"]
