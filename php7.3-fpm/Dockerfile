#FROM alpine:3
FROM php:7.3-fpm-alpine

#ENV TZ=Europe/Rome
#RUN apk add tzdata && cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && apk del tzdata

RUN apk add nginx composer php7-fpm

# Copy configuration
COPY nginx.conf /etc/nginx/
#COPY default-sites.conf /etc/nginx/conf.d/default.conf
COPY php.ini /usr/local/etc/php/php.ini
COPY timezone.ini /etc/php7/conf.d/
COPY timezone.ini /etc/php7/cli/conf.d/
RUN rm -f /etc/nginx/conf.d/default.conf

# Make log dir
RUN mkdir -p /DATA/logs/nginx

# Copy application file
COPY index.php /var/www/html/

# Entrypoint
COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh
ENTRYPOINT ["/usr/local/bin/docker-entrypoint.sh"]

EXPOSE 80