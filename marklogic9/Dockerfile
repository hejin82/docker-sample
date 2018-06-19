FROM centos:centos7

MAINTAINER hejin <hejin82@gmail.com>

ENV ML_RPM_FILE MarkLogic.rpm

ADD ${ML_RPM_FILE} /tmp/${ML_RPM_FILE}

RUN yum -y install \
    initscripts \
    /tmp/${ML_RPM_FILE} \
    python-setuptools

RUN easy_install supervisor
ADD supervisord.conf /etc/supervisord.conf

RUN yum clean all && rm -rf /tmp/*

WORKDIR /

EXPOSE 7997 7998 8000 8001 8002

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]