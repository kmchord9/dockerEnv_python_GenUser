FROM python:3.7

ARG DOCKER_UID=1000
ARG DOCKER_USER=pi
ARG DOCKER_PASSWORD=docker

RUN apt-get update && apt-get install -y sudo \
  vim && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  useradd -m --uid ${DOCKER_UID} --groups sudo ${DOCKER_USER} && \
  #usermod -G sudo ${DOCKER_USER} && \
  echo ${DOCKER_USER}:${DOCKER_PASSWORD} | chpasswd && \
  echo "${DOCKER_USER}:x:${DOCKER_UID}:${gid}:${DOCKER_USER},,,::/bin/bash" >> /etc/passwd && \
  echo "${DOCKER_USER}:x:${DOCKER_UID}:" >> /etc/group && \
  echo "Set disable_coredump false" >> /etc/sudo.conf && \
  echo export PATH='$PATH:$HOME/.yarn/bin' >> ~/.bashrc

USER ${DOCKER_USER}

ENV HOME /home/${DOCKER_USER}

CMD ["/bin/bash"] 
