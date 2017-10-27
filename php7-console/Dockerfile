FROM centos:7
MAINTAINER Jianfei Dan <dd@sinfere.com>

RUN yum -y update && yum clean all
RUN yum -y install --setopt=tsflags=nodocs epel-release && yum clean all

RUN rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
ADD remi.repo /etc/yum.repos.d/

RUN yum -y install --setopt=tsflags=nodocs php70 php70-php-bcmath php70-php-devel php70-php-fpm php70-php-gd php70-php-json php70-php-mbstring php70-php-mcrypt php70-php-xml php70-php-pecl-mongodb php70-php-pecl-zip php70-php-opcache php70-php-mysqlnd php70-php-pdo

RUN yum -y install --setopt=tsflags=nodocs  python-pip
RUN yum clean all

RUN pip install supervisor

ADD php.ini /etc/opt/remi/php70/
ADD supervisord.conf /etc/

EXPOSE 80

CMD ["/usr/bin/supervisord"]
