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

RUN sudo apt-get install -y python3 wget git python3-tk
RUN sudo apt-get install -y libsm6 libxext6
RUN sudo apt-get install -y libglib2.0-0
RUN sudo apt-get install -y vim
RUN cd /home/${username} && wget https://bootstrap.pypa.io/get-pip.py && sudo -H python3 get-pip.py && rm get-pip.py
RUN cd /home/${username} && git clone https://github.com/MaybeShewill-CV/lanenet-lane-detection
RUN sudo -H python3 -m pip install -U pip
RUN cd /home/${username}/lanenet-lane-detection && sudo -H python3 -m pip install -r requirements.txt
RUN sudo -H python3 -m pip install numpy==1.14.5
RUN sudo -H python3 -m pip install scipy

