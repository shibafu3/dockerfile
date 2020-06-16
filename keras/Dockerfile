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

RUN sudo apt-get install -y build-essential
RUN sudo apt-get install -y cmake
RUN sudo apt-get install -y zlib1g-dev
RUN sudo apt-get install -y libjpeg-dev
RUN sudo apt-get install -y libboost-all-dev
RUN sudo apt-get install -y gcc
RUN sudo apt-get install -y libsdl2-dev
RUN sudo apt-get install -y wget
RUN sudo apt-get install -y unzip
RUN sudo apt-get install -y vim
RUN sudo apt-get install -y python3-dev
RUN sudo apt-get install -y python3-pip
RUN sudo -H python3 -m pip install -U pip
RUN sudo -H python3 -m pip install keras==2.1.6
RUN sudo -H python3 -m pip install tensorflow-gpu==1.8.0
RUN sudo -H python3 -m pip install h5py==2.7.1
RUN sudo -H python3 -m pip install gevent==1.2.2
RUN sudo -H python3 -m pip install opencv-python==3.3.1.11
RUN sudo -H python3 -m pip install matplotlib==2.1.1
RUN sudo -H python3 -m pip install PIllow==5.1.0
RUN sudo -H python3 -m pip install pandas==0.22.0
RUN sudo -H python3 -m pip install gensim==3.2.0
RUN sudo -H python3 -m pip install nltk==3.2.5
RUN sudo -H python3 -m pip install scikit-learn==0.19.1
RUN sudo -H python3 -m pip install sklearn==0.0
RUN sudo -H python3 -m pip install gym==0.10.5
RUN sudo -H python3 -m pip install pygame==1.9.3
RUN sudo -H python3 -m pip install doom_py==0.0.15
# RUN sudo -H python3 -m pip install  quiver-engine==0.1.4.1.4

ENV CUDA_HOME=/usr/local/cuda
ENV PATH=$PATH:${CUDA_HOME}/bin
ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${CUDA_HOME}/lib64

RUN mkdir -p /home/${username}/Documents/deeplearning
