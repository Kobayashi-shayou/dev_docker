FROM php:8.1-fpm

# ユーザーを作成
ARG UID=1000
ARG GID=1000
RUN useradd -m -u ${UID} docker

# composerをインストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Laravelに必要なパッケージをインストール
RUN apt-get update && apt-get install -y git zip unzip

RUN apt-get update \
    && docker-php-ext-install pdo_mysql

# 作成したユーザーに切り替える
USER ${UID}:${GID}

# 作業ディレクトリを変更
WORKDIR /var/www/html
