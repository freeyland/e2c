FROM    alpine:3.10

LABEL   maintainer="Emma2Click, Frederick Eyland"

ENV     COMPOSER_ALLOW_SUPERUSER=1
ENV     E2C_CFG_C_UID=${E2C_CFG_C_UID:-1000}
ENV     E2C_CFG_C_GID=${E2C_CFG_C_GID:-1000}

COPY    common/conf/php.ini /etc/php7/conf.d/
COPY    common/conf/php-fpm.conf /etc/php7/
COPY    common/conf/supervisor.conf /etc/
COPY    common/bin/* /usr/local/bin/

RUN     apk update && \
        apk add --no-cache \
            shadow \
            php7 \
            php7-bcmath \
            php7-calendar \
            php7-ctype \
            php7-curl \
            php7-dom \
            php7-fpm \
            php7-gd \
            php7-gettext \
            php7-iconv \
            php7-intl \
            php7-json \
            php7-mbstring \
            php7-mysqli \
            php7-opcache \
            php7-openssl \
            php7-pdo_mysql \
            php7-simplexml \
            php7-soap \
            php7-sockets \
            php7-sodium \
            php7-tokenizer \
            php7-xml \
            php7-xmlwriter \
            php7-xsl \
            php7-zip \
            php7-pecl-amqp \
            php7-pecl-igbinary \
            php7-pecl-mcrypt \
            php7-pecl-redis \
            php7-pecl-ssh2 \
            composer \
            curl \
            bash \
            git \
            gzip \
            lsof \
            npm \
            supervisor && \
        \
        \
        set -ex && cd /tmp && \
        curl -O https://files.magerun.net/n98-magerun2.phar && \
        mv n98-magerun2.phar /usr/local/bin/ && \
        chmod +x /usr/local/bin/n98-magerun2.phar && \
        \
        \
        rm -rf /var/cache/apk/* && \
        rm -rf /tmp/* && \
        \
        \
        addgroup -g 1000 -S app && \
        adduser -u 1000 -S app -G app -h /var/www -s /bin/bash && \
        echo 'export PS1="\w $ "' > /var/www/.bashrc && \
        \
        \
        mkdir -p /var/www/html /var/www/.config /var/www/.npm /sock && \
        touch /var/spool/cron/crontabs/app && \
        chown -R app:app /var/www /var/www/.bashrc /var/www/.config \
            /var/www/.npm /etc/php7/conf.d /sock /var/log \
            /usr/local/bin/n98-magerun2.phar && \
        chmod +x /usr/local/bin/docker-host /usr/local/bin/docker-php-entrypoint && \
        \
        \
        ln -sf /var/www/html/node_modules/grunt/bin/grunt /usr/bin/grunt && \
        ln -sf /usr/local/bin/n98-magerun2.phar /usr/local/bin/n98-magerun2 && \
        ln -sf /usr/sbin/php-fpm7 /usr/sbin/php-fpm && \
        ln -sf /etc/init.d/php-fpm7 /etc/init.d/php-fpm

ENTRYPOINT ["docker-php-entrypoint"]

WORKDIR /var/www/html

CMD     docker-host; supervisord -c /etc/supervisor.conf