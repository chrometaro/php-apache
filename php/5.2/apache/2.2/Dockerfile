FROM centos:5.11

MAINTAINER Chrometaro <chrometaro@gmail.com>

COPY ./yum.repos.d/ /etc/yum.repos.d/

ADD https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL /etc/pki/rpm-gpg/RPM-GPG-KEY-PGDG
ADD https://ftp.postgresql.org/pub/binary/v8.4.2/linux/rpms/redhat/rhel-5-x86_64/compat-postgresql-libs-4-1PGDG.rhel5.x86_64.rpm  ./
RUN rpm -i compat-postgresql-libs-4-1PGDG.rhel5.x86_64.rpm \
 && rm compat-postgresql-libs-4-1PGDG.rhel5.x86_64.rpm

RUN yum update -y \
 && yum install -y \
    php \
    php-devel \
    php-gd \
    php-mbstring \
    php-mysql \
    php-odbc \
    php-pdo \
    php-pear \
    php-pgsql \
    php-xml \
    sudo \
 && pear install \
    Mail-1.2.0 \
    Mail_Mime-1.8.1 \
    Archive_Zip-0.1.1 \
    DB-1.7.13 \
    OLE-1.0.0RC1 \
    HTTP_Request

COPY httpd-foreground /usr/local/bin/

EXPOSE 22 80 443
CMD ["httpd-foreground"]