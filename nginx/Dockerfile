FROM nginx:stable-alpine

ENV NGINX_DIR=/etc/nginx
USER root
# Update dan install dependensi yang dibutuhkan (tidak ada openssl)
RUN echo "https://dl-cdn.alpinelinux.org/alpine/v3.21/main" > /etc/apk/repositories && \
    echo "https://dl-cdn.alpinelinux.org/alpine/v3.21/community" >> /etc/apk/repositories && \
    apk update && \
    apk upgrade && \
    mkdir -p ${NGINX_DIR}/conf.d

# Salin konfigurasi dan file HTML ke dalam image
COPY setup/nginx.conf ${NGINX_DIR}/nginx.conf
COPY setup/default.conf ${NGINX_DIR}/conf.d/
COPY setup/index.html /usr/share/nginx/html/index.html
COPY setup/error.html /usr/share/nginx/html/error.html

# Jalankan Nginx di foreground
CMD ["nginx", "-g", "daemon off;"]
