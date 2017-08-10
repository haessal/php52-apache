FROM centos:6

MAINTAINER haessal@mizutamauki.net

RUN yum -y install wget gcc openssl-devel
RUN cd /usr/local/src && \
wget http://www-us.apache.org/dist//httpd/httpd-2.2.34.tar.gz && \
tar zxvf httpd-2.2.34.tar.gz
RUN cd /usr/local/src/httpd-2.2.34 && \
./configure --prefix=/usr/local/apache2/ --enable-so --enable-rewrite --enable-ssl && \
make && make install

ENTRYPOINT /usr/local/apache2/bin/httpd -D FOREGROUND
