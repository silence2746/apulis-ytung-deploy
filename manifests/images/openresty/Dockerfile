FROM ubuntu:18.04
RUN apt update \
    && apt-get install -y libpcre3-dev libssl-dev perl make build-essential curl wget git vim \
    && wget https://openresty.org/download/openresty-1.15.8.3.tar.gz \
    && tar zxf openresty-1.15.8.3.tar.gz \
    && cd openresty-1.15.8.3 && ./configure --without-http_gzip_module \
    && make && make install
WORKDIR /usr/local/openresty
RUN git clone https://github.com/spacewander/lua-resty-base-encoding.git && cd lua-resty-base-encoding && make && cp librestybaseencoding.so ../site/lualib/ && cd .. && rm lua-resty-base-encoding -rf

ADD config/nginx/nginx.conf /usr/local/openresty/nginx/conf/nginx.conf
ADD lib/resty /usr/local/openresty/nginx/jwt-lua/resty
ADD start.sh /
RUN apt update && apt install -y vim && chmod +x /start.sh

