ARG     NGINX_VERSION=${NGINX_VERSION:-1.17}

FROM    nginx:${NGINX_VERSION}-alpine

LABEL   maintainer="Emma2click,Frederick Eyland freeyland@gmail.com"

ENV     E2C_CFG_C_UID=${E2C_CFG_C_UID:-1000}
ENV     E2C_CFG_C_GID=${E2C_CFG_C_GID:-1000}

COPY    common/bin/* /usr/local/bin/
COPY    conf/nginx.conf /etc/nginx/nginx.conf
COPY    conf/conf.d/default.conf /etc/nginx/conf.d/default.conf

RUN     apk update && \
        apk add --no-cache \
        shadow && \
        addgroup -S -g 1000 app && \
        adduser -S -g 1000 -u 1000 -h /var/www -s /bin/ash app && \
        touch /var/run/nginx.pid && \
        mkdir /sock && \
    	chown -R app:app /var/cache/nginx /var/run/nginx.pid \
    		/etc/nginx/nginx.conf /etc/nginx/conf.d /sock && \
        chmod +x /usr/local/bin/docker-nginx-entrypoint

USER    app:app

#ENTRYPOINT ["docker-nginx-entrypoint"]

WORKDIR /var/www/html