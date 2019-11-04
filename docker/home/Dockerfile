ARG     NGINX_VERSION=${NGINX_VERSION:-1.17}

FROM    nginx:${NGINX_VERSION}-alpine

LABEL   maintainer="Emma2click,Frederick Eyland freeyland@gmail.com"


CMD ["nginx" "-g" "daemon off;"]


COPY file:5f0d302829d62fe5b3cc3095454568823288724f8ea0d889e1a1db925f6c8dcd in /etc/nginx/conf.d/ 

COPY file:29b8348431986c7b62a8bcc7daade100320137d497e1838c3d336d3f52ae093b in /usr/share/nginx/html/ 

COPY file:acee8672dff1d31a8632984d651838daf6caf44d66cc4c0e98731138d6ae5903 in /nginx 


- ~/.m2c/www/default.conf:/etc/nginx/conf.d/default.conf
      - ~/.m2c/www/html/index.html:/usr/share/nginx/html/index.html

COPY    conf/nginx.conf /etc/nginx/nginx.conf
COPY    conf/default.conf /etc/nginx/conf.d/default.conf
COPY    index.html  /usr/share/nginx/html/index.html

RUN apk update && \             
apk add --no-cache openssh && \
rm -rf /var/cache/apk/* && \ 
rm -rf /tmp/* && \
chmod +x /nginx &&  \
adduser -D -s /bin/ash user && \ 
passwd -u user && \
echo "" > /etc/motd && \ 
echo "" >> /etc/ssh/sshd_config && \ 
echo "PermitRootLogin no" >> /etc/ssh/sshd_config && \ 
echo "PermitTTY no" >> /etc/ssh/sshd_config && \
echo "ForceCommand /sbin/nologin" >> /etc/ssh/sshd_config && \
echo "" >> /etc/ssh/sshd_config && \ 
echo "Match User user" >> /etc/ssh/sshd_config && \
echo "AllowTcpForwarding yes" >> /etc/ssh/sshd_config && \
echo "PermitEmptyPasswords yes" >> /etc/ssh/sshd_config && \
echo "PermitTTY no" >> /etc/ssh/sshd_config && \
echo "ForceCommand /sbin/nologin" >> /etc/ssh/sshd_config && \
ssh-keygen -A

ENTRYPOINT ["/bin/sh" "-c" "/nginx"]