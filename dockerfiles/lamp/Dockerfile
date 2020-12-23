FROM ubuntu

ENV DEBIAN_FRONTEND noninteractive

RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  apt-get clean

RUN apt-get update

RUN apt-get -y install software-properties-common \
    && add-apt-repository -y ppa:ondrej/php \
    && apt-get install --assume-yes apt-utils \
    && apt-get -y install php7.4 \
    && apt-get -y install php7.4-fpm \
    && apt-get -y install nginx \
    && apt-get -y install composer \
    && apt-get -y install vim \
    && apt-get -y install mysql-server \
    && apt-get -y install mysql-client \
    && apt-get -y install libmysqlclient-dev 

WORKDIR /data/work

