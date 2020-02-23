FROM alpine:3.11
MAINTAINER noc@lpweb.it

COPY nginxctl.sh /usr/local/bin/

RUN apk add --update --no-cache curl

RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.0-linux-x86_64.tar.gz && tar xzvf filebeat-7.6.0-linux-x86_64.tar.gz && rm -rf filebeat-7.6.0-linux-x86_64.tar.gz && mv filebeat-7.6.0-linux-x86_64 /etc/filebeat

RUN apk add --update --no-cache nginx

COPY etc/nginx/nginx.conf /etc/nginx/
COPY etc/nginx/conf.d/symfony.conf /etc/nginx/conf.d/
COPY etc/nginx/conf.d/upstream.conf /etc/nginx/conf.d/

RUN adduser -D -g '' -G www-data www-data

COPY etc/filebeat/filebeat.yml /etc/filebeat/filebeat.yml
RUN chmod go-w /etc/filebeat/filebeat.yml

CMD ["/usr/local/bin/nginxctl.sh"]

EXPOSE 80
