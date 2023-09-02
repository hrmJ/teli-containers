FROM node:16
WORKDIR /usr/src/app
RUN wget https://dl.yarnpkg.com/debian/pubkey.gpg 
RUN apt-key add pubkey.gpg
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN  apt-get update && apt-get install --no-install-recommends yarn

ENTRYPOINT cd project && /usr/bin/yarn watch



