FROM nvidia/cuda:11.8.0-cudnn8-devel-ubuntu20.04

RUN apt-get -y update
RUN apt-get install -y --no-install-recommends \
    apt-utils \
    vim \
    nano \
    tmux
RUN apt-get -y autoremove && apt-get -y autoclean
