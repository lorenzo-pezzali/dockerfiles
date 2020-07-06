FROM php:7.3-alpine

LABEL maintener="noc@lpweb.it"

ENV TZ=Europe/Rome
RUN apk add tzdata && cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && apk del tzdata

RUN apk add --update --no-cache \
    coreutils \
    apache-ant \
    nodejs \
    python2 \
    gcc \
    make \
    curl

RUN echo "$(curl -sS https://composer.github.io/installer.sig) -" > composer-setup.php.sig \
        && curl -sS https://getcomposer.org/installer | tee composer-setup.php | sha384sum -c composer-setup.php.sig \
        && php composer-setup.php && rm composer-setup.php* \
        && chmod +x composer.phar && mv composer.phar /usr/bin/composer