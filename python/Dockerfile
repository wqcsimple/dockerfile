FROM centos:7
MAINTAINER whis Wang <wqcsimple@foxmail.com>

RUN yum -y update && yum clean all
RUN yum -y install --setopt=tsflags=nodocs epel-release && yum clean all

RUN yum -y install --setopt=tsflags=nodocs  python-pip

#RUN yum groupinstall 'Development Tools' -y
#RUN yum install zlib-devel bzip2-devel  openssl-devel ncurses-devel gcc wget -y
#RUN wget https://www.python.org/ftp/python/3.6.0/Python-3.6.0.tgz
#RUN tar -zxvf Python-3.6.0.tgz
#RUN cd Python-3.6.0 && ./configure --prefix=/usr/local/python3
#RUN make && make install

# 替换yum
#ADD yum /usr/bin/

# 替换python2
#RUN rm -rf /usr/bin/python
#RUN rm -rf /usr/bin/pip
#RUN ln -sv  /usr/local/python3/bin/python3 /usr/bin/python
#RUN ln -sv  /usr/local/python3/bin/pip3 /usr/bin/pip
#RUN pip install workbook psutil urllib3 requests  Scrapy PyMySQL pymongo pycparser  parsel lxml html5lib beautifulsoup4

RUN yum clean all

RUN pip install supervisor

ADD supervisord.conf /etc/

CMD ["/usr/bin/supervisord"]
