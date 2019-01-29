FROM ubuntu:16.04
RUN apt-get update
RUN apt-get install -y software-properties-common

RUN mkdir /opt/hands_on

# setup.shのadd-apt-repositoryをRUNでするとこける
COPY ./setup.sh /opt/hands_on
RUN bash /opt/hands_on/setup.sh
RUN apt-get install -y --allow-unauthenticated php7.1 memcached php7.1-common php7.1-mysql php7.1-memcache php7.1-memcached php7.1-curl php7.1-intl php7.1-gd
RUN apt-get install -y --allow-unauthenticated php7.1-mbstring
RUN apt-get install -y --allow-unauthenticated php7.1-xml

# 何故かcliが7.3なので削除する、7.1に自動で変わる
RUN apt-get remove -y php7.3-cli

RUN apt-get install -y curl

RUN curl -sS https://getcomposer.org/installer | php; mv composer.phar /usr/local/bin/composer

RUN apt-get install -y mysql-client

RUN apt-get install -y git