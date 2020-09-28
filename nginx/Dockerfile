FROM ubuntu:18.04

RUN apt-get -y update
RUN apt-get install -y wget build-essential libpcre3 libpcre3-dev libssl-dev ffmpeg

WORKDIR /build

RUN wget https://nginx.org/download/nginx-1.18.0.tar.gz

RUN tar -xvf ./nginx-1.18.0.tar.gz

RUN wget https://github.com/arut/nginx-rtmp-module/archive/v1.2.1.tar.gz

RUN tar -xvf ./v1.2.1.tar.gz

WORKDIR nginx-1.18.0

RUN apt-get install zlib1g-dev

RUN ./configure --add-module=/build/nginx-rtmp-module-1.2.1
RUN make
RUN make install


ADD ./nginx.conf /usr/local/nginx/conf/nginx.conf

RUN mkdir /tmp/hls

CMD /usr/local/nginx/sbin/nginx -g "daemon off;"

