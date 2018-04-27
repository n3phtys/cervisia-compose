FROM liuchong/rustup:nightly
RUN apt-get update
RUN apt-get install -y build-essential libssl-dev curl git

RUN apt-get install -y sudo bash gnupg apt-file

RUN apt-get install -y pkg-config libssl-dev apt-utils nano

RUN apt-get update
RUN printenv

RUN apt list --installed

RUN ls -la /usr/include
RUN ls -la /usr/include/openssl
RUN ls -la /usr
RUN ls -la /usr/lib
RUN ls -la /usr/local/ssl
RUN ls -la /usr/lib
RUN ls -la /usr/lib/ssl

#RUN sleep 10



RUN curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

RUN apt-get install -y nodejs 

RUN npm install -g @angular/cli

RUN npm --version
RUN git --version
RUN cargo --version

WORKDIR /root/.cervisia-server/
WORKDIR /usr/cervisia/frontend/
WORKDIR /usr/cervisia/backend/
WORKDIR /usr/cervisia/

RUN git clone https://github.com/n3phtys/ng-cervisia --depth 1
WORKDIR /usr/cervisia/ng-cervisia
RUN ls -la .
RUN npm install
RUN ng build --prod --base-href /bierliste-test/
WORKDIR /usr/cervisia/
RUN rm -rf /usr/cervisia/frontend
RUN mkdir /usr/cervisia/frontend
RUN ls -la /usr/cervisia/ng-cervisia
RUN cp -a /usr/cervisia/ng-cervisia/dist/. /usr/cervisia/frontend/
RUN rm -rf ng-cervisia

RUN git clone https://github.com/n3phtys/cervisia-server --depth 1
WORKDIR /usr/cervisia/cervisia-server



RUN export OPENSSL_INCLUDE_DIR=/usr/include/openssl && export OPENSSL_LIB_DIR=/usr/lib/x86_64-linux-gnu && export OPENSSL_STATIC=1 && ls -la /usr/lib/ssl && apt-file list libssl-dev && printenv && cargo build --release

WORKDIR /usr/cervisia/
RUN rm -rf /usr/cervisia/backend
RUN mkdir /usr/cervisia/backend
RUN ls -la /usr/cervisia/cervisia-server/target/release
RUN cp -a /usr/cervisia/cervisia-server/target/release/cervisia-server /usr/cervisia/backend/
RUN rm -rf cervisia-server
