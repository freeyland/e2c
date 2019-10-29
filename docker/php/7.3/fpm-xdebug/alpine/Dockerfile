FROM    alpine:3.10

LABEL   maintainer="Emma2click, Dmitry Shkoliar @shkoliar"

ENV     E2C_CFG_C_UID=${E2C_CFG_C_UID}
ENV     E2C_CFG_C_GID=${E2C_CFG_C_GID}

COPY    common/conf-xdebug/php.ini /etc/php7/conf.d/
COPY    common/conf-xdebug/php-fpm.conf /etc/php7/
COPY    common/conf-xdebug/supervisor.conf /etc/
COPY    common/bin/* /usr/local/bin/

RUN     apk update && \
apk add --no-cache \
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
php7-pecl-xdebug \
curl \
gzip \
lsof \
supervisor && \
\
\
sed -i -e 's/^;zend_extension/\zend_extension/g' /etc/php7/conf.d/xdebug.ini && \
\
\
rm -rf /var/cache/apk/* && \
rm -rf /tmp/* && \
\
\
addgroup -g 1000 -S app && \
adduser -u 1000 -S app -G app -h /var/www -s /bin/bash && \
\
\
mkdir -p /var/www/html /var/www/.config /sock && \
touch /var/spool/cron/crontabs/app && \
chown -R app:app /var/www/html /var/www/.config \
/etc/php7/conf.d /sock /var/log && \
chmod +x /usr/local/bin/docker-host /usr/local/bin/docker-php-entrypoint && \
\
\
ln -sf /usr/sbin/php-fpm7 /usr/sbin/php-fpm && \
ln -sf /etc/init.d/php-fpm7 /etc/init.d/php-fpm

ENTRYPOINT ["docker-php-entrypoint"]

WORKDIR /var/www/html

CMD     docker-host; supervisord -c /etc/supervisor.conf