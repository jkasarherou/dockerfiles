from centos:7

ARG AWS_S3_HOST
ARG AWS_S3_PORT

RUN rm -rf /var/cache/yum
RUN yum -y clean all
RUN yum -y install deltarpm

RUN yum -y update

RUN yum -y install epel-release
RUN yum -y install git python-pip python-virtualenv

RUN git clone https://github.com/s3tools/s3cmd

RUN mkdir /root/.aws

COPY config /root/.aws/config
COPY credentials /root/.aws/credentials

COPY s3.cfg /

CMD echo "${AWS_S3_IP} s3host" >> /etc/hosts && \
    cd /s3cmd && \
    ./run-tests.py --config /s3.cfg
