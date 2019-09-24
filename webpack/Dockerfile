FROM ubuntu:latest

WORKDIR /app

RUN apt update && apt install curl gnupg software-properties-common -y &&\
    rm -rf /var/lib/apt/lists/*

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list 

RUN curl  https://install-node.now.sh/lts -o node.sh 
RUN bash node.sh --yes 
RUN apt update && apt install -y yarn &&\
    rm -rf /var/lib/apt/lists/*

#RUN yarn
CMD yarn install && yarn start-dev
