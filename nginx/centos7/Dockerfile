FROM centos:7
MAINTAINER Jianfei Dan <dd@sinfere.com>

RUN yum -y update && yum clean all
RUN yum -y install --setopt=tsflags=nodocs epel-release && yum clean all

ADD nginx.repo /etc/yum.repos.d/

RUN yum -y install --setopt=tsflags=nodocs  nginx python-pip
RUN yum clean all

RUN pip install supervisor

ADD nginx.conf /etc/nginx
ADD supervisord.conf /etc/

EXPOSE 80

CMD ["/usr/bin/supervisord"]
