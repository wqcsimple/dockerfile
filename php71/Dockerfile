FROM centos:7
MAINTAINER Whis Wang <admin@wwhis.com>

ENV TZ 'Asia/Shanghai'

RUN yum -y update && yum clean all
RUN yum -y install --setopt=tsflags=nodocs epel-release && yum clean all

RUN rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
ADD remi.repo /etc/yum.repos.d/

RUN yum install tzdata -y
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "$TZ" > /etc/timezone

RUN yum -y install --setopt=tsflags=nodocs \
    php71 php71-php-bcmath php71-php-devel php71-php-fpm \
    php71-php-gd php71-php-json php71-php-mbstring  \
    php71-php-mcrypt php71-php-xml php71-php-pecl-mongodb \
    php71-php-pecl-zip php71-php-opcache php71-php-mysqlnd php71-php-pdo

ADD nginx.repo /etc/yum.repos.d/
RUN yum -y install --setopt=tsflags=nodocs  nginx

RUN yum -y install --setopt=tsflags=nodocs  python-pip
RUN yum clean all

RUN pip install --upgrade pip
RUN pip install supervisor

ADD nginx.conf /etc/nginx
ADD php.ini /etc/opt/remi/php71/
ADD php-fpm/php-fpm.d/www.conf /etc/opt/remi/php71/php-fpm.d/
ADD php-fpm/php-fpm.conf /etc/opt/remi/php71/
ADD supervisord.conf /etc/

RUN chown -R nginx:nginx /var/opt/remi/php71/lib/php/session

EXPOSE 80

CMD ["/usr/bin/supervisord"]
