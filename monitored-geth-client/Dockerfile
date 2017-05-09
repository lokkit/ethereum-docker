FROM ubuntu:16.04

RUN apt update && \
  apt install -y software-properties-common && \
  add-apt-repository -y ppa:ethereum/ethereum && \
  apt update && \
  apt install -y ethereum

EXPOSE 8545
EXPOSE 30303


RUN apt-get update &&\
    apt-get install -y curl git-core &&\
    curl -sL https://deb.nodesource.com/setup_4.x | bash - &&\
    apt-get update &&\
    apt-get install -y nodejs

RUN cd /root &&\
    git clone https://github.com/cubedro/eth-net-intelligence-api &&\
    cd eth-net-intelligence-api &&\
    npm install &&\
    npm install -g pm2

ADD start.sh /root/start.sh
ADD app.json /root/eth-net-intelligence-api/app.json
RUN chmod +x /root/start.sh

ENTRYPOINT /root/start.sh
