FROM nginx:1.27.0-alpine

ARG NGINX_HOST
ARG NGINX_LISTEN_PORT

COPY ./templates /etc/nginx/templates

RUN envsubst '\$NGINX_HOST,\$NGINX_LISTEN_PORT' < /etc/nginx/templates/nginx.conf.template