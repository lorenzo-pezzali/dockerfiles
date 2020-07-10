FROM postgres:12-alpine

RUN apk update
RUN apk add --update --no-cache postgis

ENV TZ Europe/Rome
ENV LANG it_IT.UTF-8
ENV LANGUAGE it_IT.UTF-8
ENV LC_ALL it_IT.UTF-8

RUN apk add tzdata && cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && apk del tzdata

#RUN /usr/glibc-compat/bin/localedef -i it_IT -c -f UTF-8 -A /usr/share/locale/locale.alias it_IT.UTF-8