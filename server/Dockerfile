FROM node:22 AS stage-one

# Install DEB dependencies and others.
RUN \
	set -x \
	&& apt-get update \
	&& apt-get install -y net-tools build-essential python3 python3-pip valgrind

WORKDIR /service

COPY server/package.json .
RUN npm install
COPY server/server.js .
COPY server/config.js .
COPY server/lib lib
COPY server/certs certs

CMD ["node", "/service/server.js"]
