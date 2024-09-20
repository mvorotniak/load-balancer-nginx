FROM nginx:alpine

RUN apk add --no-cache \
    build-base \
    curl \
    git \
    libmaxminddb \
    libmaxminddb-dev \
    geoip \
    geoip-dev \
    pcre-dev \
    zlib-dev \
    openssl-dev

RUN curl -O http://nginx.org/download/nginx-1.27.1.tar.gz \
    && tar -xzvf nginx-1.27.1.tar.gz \
    && cd nginx-1.27.1 \
    && git clone https://github.com/leev/ngx_http_geoip2_module.git  \
    && ./configure --with-compat --add-dynamic-module=ngx_http_geoip2_module \
    && make modules \
    && cp objs/ngx_http_geoip2_module.so /etc/nginx/modules/ \
    && make clean 

COPY ./GeoLite2-Country.mmdb /etc/nginx/GeoLite2-Country.mmdb
