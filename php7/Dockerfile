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

RUN yum -y install --setopt=tsflags=nodocs php70 php70-php-bcmath php70-php-devel php70-php-fpm php70-php-gd php70-php-json php70-php-mbstring php70-php-mcrypt php70-php-xml php70-php-pecl-mongodb php70-php-pecl-zip php70-php-opcache php70-php-mysqlnd php70-php-pdo

ADD nginx.repo /etc/yum.repos.d/
RUN yum -y install --setopt=tsflags=nodocs  nginx

RUN yum -y install --setopt=tsflags=nodocs  python-pip
RUN yum clean all

RUN pip install supervisor

ADD nginx.conf /etc/nginx
ADD php.ini /etc/opt/remi/php70/
ADD php-fpm/php-fpm.d/www.conf /etc/opt/remi/php70/php-fpm.d/
ADD php-fpm/php-fpm.conf /etc/opt/remi/php70/
ADD supervisord.conf /etc/

RUN chown -R nginx:nginx /var/opt/remi/php70/lib/php/session

EXPOSE 80

CMD ["/usr/bin/supervisord"]
