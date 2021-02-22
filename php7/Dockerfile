FROM php:7.4-apache

# 環境の更新と必要なモジュールをインストール
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim \
libpng-dev \
libpq-dev \
&& docker-php-ext-install pdo_mysql mysqli

# Composerをインストール
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

# php.iniをホスト側に追加
ADD php.ini /usr/local/etc/php/
ADD ./conf/000-default.conf /etc/apache2/sites-enabled/


# modRewrite
RUN mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled
RUN /bin/sh -c a2enmod rewrite
