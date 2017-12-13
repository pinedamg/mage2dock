FROM nginx:alpine

MAINTAINER Mahmoud Zalt <mahmoud@zalt.me>

ADD nginx.conf /etc/nginx/

ARG PHP_UPSTREAM_CONTAINER=php-fpm
ARG PHP_UPSTREAM_PORT=9000

COPY certs/ /etc/nginx/ssl/

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data

# Set upstream conf and remove the default conf
RUN echo "upstream php-upstream { server ${PHP_UPSTREAM_CONTAINER}:${PHP_UPSTREAM_PORT}; }" > /etc/nginx/conf.d/upstream.conf
## && rm /etc/nginx/conf.d/default.conf

RUN sed -i "s/{$MAGENTO_RUN_MODE}/${MAGENTO_RUN_MODE}/" /etc/nginx/conf.d/default.conf
RUN sed -i "s/{$UPLOAD_MAX_FILESIZE}/${UPLOAD_MAX_FILESIZE}/" /etc/nginx/conf.d/default.conf

CMD ["nginx"]

EXPOSE 80 443
