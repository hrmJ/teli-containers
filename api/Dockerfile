FROM ubuntu:18.04

ENV DOCKER_USER developer
RUN apt update
RUN apt install -y sudo
RUN adduser --disabled-password --gecos '' "$DOCKER_USER" 
RUN adduser "$DOCKER_USER" sudo && \
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers && \
    touch /home/$DOCKER_USER/.sudo_as_admin_successful && \
    rm -rf /var/lib/apt/lists/*

USER "$DOCKER_USER"
WORKDIR "/home/$DOCKER_USER"

#NVM >>> NODE

RUN sudo apt update && sudo apt install -y wget gnupg curl
RUN wget https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh 
RUN chmod +x install.sh && ./install.sh
ENV NVM_DIR /home/$DOCKER_USER/.nvm
RUN . "$NVM_DIR/nvm.sh" && \
    nvm install --lts && \
    nvm alias default stable
##YARN

RUN wget https://dl.yarnpkg.com/debian/pubkey.gpg 
RUN sudo apt-key add pubkey.gpg
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
RUN sudo apt-get update && sudo apt-get install --no-install-recommends yarn
RUN curl  https://install-node.now.sh/lts -o node.sh 
RUN sudo bash node.sh --yes 

RUN sudo ln -s /home/developer/.nvm/versions/node/v10.16.3/bin/node /usr/bin/node 

ENTRYPOINT cd project && /usr/bin/yarn watch
#CMD ['watch']



