FROM centos:6

MAINTAINER haessal@mizutamauki.net

RUN yum -y install wget gcc openssl-devel perl libxml2 libxml2-devel mysql mysql-server mysql-devel
RUN mkdir -p /replace/with/path/to/perl/ && ln -s /usr/bin/perl /replace/with/path/to/perl/interpreter
RUN cd /usr/local/src && \
wget http://www-us.apache.org/dist//httpd/httpd-2.2.34.tar.gz && \
tar zxvf httpd-2.2.34.tar.gz && \
wget http://museum.php.net/php5/php-5.2.5.tar.gz && \
tar zxvf php-5.2.5.tar.gz
RUN cd /usr/local/src/httpd-2.2.34 && \
./configure --prefix=/usr/local/apache2/ --enable-so --enable-rewrite --enable-ssl && \
make && make install
RUN cd /usr/local/src/php-5.2.5 && \
./configure \
--prefix=/usr/local/php5 \
--with-apxs2=/usr/local/apache2/bin/apxs \
--without-sqlite \
--enable-mbstring \
--enable-zend-multibyte \
--enable-ftp \
--enable-sockets \
--with-mysql=/usr/bin/ \
--with-libdir=lib64 \
--with-zlib && \
make && make test && make install

ENTRYPOINT /usr/local/apache2/bin/httpd -D FOREGROUND
