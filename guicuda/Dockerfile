FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

ARG uid=1000
ARG gid=1000
ARG username=shiba

RUN apt-get update && apt-get install -y sudo

# Replace 1000 with your user / group id
RUN mkdir -p /home/${username} && \
    echo "${username}:x:${uid}:${gid}:${username},,,:/home/${username}:/bin/bash" >> /etc/passwd && \
    echo "${username}:x:${uid}:" >> /etc/group && \
    echo "${username} ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/${username} && \
    chmod 0440 /etc/sudoers.d/${username} && \
    chown ${uid}:${gid} -R /home/${username}


USER ${username}
ENV HOME /home/${username}
