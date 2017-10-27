FROM centos:7
MAINTAINER Jianfei Dan <dd@sinfere.com>

RUN yum -y update && yum clean all
RUN yum -y install --setopt=tsflags=nodocs epel-release && yum clean all

RUN curl --silent --location https://rpm.nodesource.com/setup_6.x | bash -
RUN yum install -y nodejs

RUN yum -y install --setopt=tsflags=nodocs  python-pip
RUN yum clean all

RUN pip install supervisor
RUN pip install supervisor-stdout

ADD supervisord.conf /etc/

CMD ["/usr/bin/supervisord"]
