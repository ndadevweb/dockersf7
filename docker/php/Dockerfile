FROM php:8.2-fpm-alpine

ARG HOST_UID
ARG HOST_GID

ENV DOCKER_CUSTOM_USER=dockeruserphp

RUN addgroup -g $HOST_GID $DOCKER_CUSTOM_USER && \
    adduser -D -u $HOST_UID -G $DOCKER_CUSTOM_USER $DOCKER_CUSTOM_USER

RUN apk add --no-cache curl bash git icu-dev
RUN docker-php-ext-install opcache intl pdo_mysql
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

RUN curl -sS https://getcomposer.org/download/2.7.2/composer.phar -o /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer

USER root
RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN chown $DOCKER_CUSTOM_USER:$DOCKER_CUSTOM_USER /root/.symfony5/bin/symfony
RUN chmod +x /root/.symfony5/bin/symfony
RUN mv /root/.symfony5/bin/symfony /usr/local/bin

USER $DOCKER_CUSTOM_USER

WORKDIR /app

CMD ["php-fpm"]
