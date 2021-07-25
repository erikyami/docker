FROM amazonlinux:2

MAINTAINER Erik Silva erikyami@gmail.com

LABEL description="A basic Apache container on AmazonLinux:2"

ENV PORT 8080

RUN yum install -y httpd && \
    yum clean all && rm -rf /var/cache/yum

RUN sed -ri -e "/^Listen 80/c\Listen ${PORT}" /etc/httpd/conf/httpd.conf && \
    chown -R apache:apache /etc/httpd/logs/ && \
    chown -R apache:apache /run/httpd/

WORKDIR /var/www/html
USER apache

EXPOSE ${PORT}

COPY ./src/ /var/www/html/

CMD ["httpd", "-D", "FOREGROUND"]
