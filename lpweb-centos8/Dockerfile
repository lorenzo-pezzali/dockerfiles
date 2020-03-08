FROM centos:8

MAINTAINER noc@lpweb.it

ENV TZ=Europe/Rome

RUN yum clean all && \
	yum -y update && \
	yum clean all && \
	ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone