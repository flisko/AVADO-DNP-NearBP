FROM --platform=linux/amd64 nearprotocol/nearcore:2.6.5

RUN apt-get update
RUN apt-get install -y wget
RUN apt-get clean

WORKDIR /app
RUN wget https://github.com/peak/s5cmd/releases/download/v1.4.0/s5cmd_1.4.0_Linux-64bit.tar.gz
RUN tar zxvf s5cmd_1.4.0_Linux-64bit.tar.gz
RUN ls /app
RUN rm /app/*.gz

COPY files/entrypoint.sh /app/entrypoint.sh
RUN chmod +x /app/entrypoint.sh

# default config
COPY files/config.json /app/config.json.default
COPY files/genesis.json /app/genesis.json

# COPY files/config.json /root/.near/config.json.default

ENTRYPOINT /app/entrypoint.sh
