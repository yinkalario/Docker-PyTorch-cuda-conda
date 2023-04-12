FROM pytorch:20.08-py3-cuda11

## other packages
RUN apt-get -y update
RUN apt-get install -y --no-install-recommends \
    apt-utils \
    vim \
    nano \
    tmux \
	curl
RUN apt-get -y autoremove && apt-get -y autoclean

## Conda
# Use the above args during building https://docs.docker.com/engine/reference/builder/#understand-how-arg-and-from-interact
ARG CONDA_VER=latest
ARG OS_TYPE=x86_64
# Install miniconda to /miniconda
RUN curl -LO "http://repo.continuum.io/miniconda/Miniconda3-${CONDA_VER}-Linux-${OS_TYPE}.sh"
RUN bash Miniconda3-${CONDA_VER}-Linux-${OS_TYPE}.sh -b -p /miniconda 
RUN rm Miniconda3-${CONDA_VER}-Linux-${OS_TYPE}.sh
ENV PATH=/miniconda/bin:${PATH}
RUN conda update -y conda
RUN conda init bash
RUN bash -c "source /root/.bashrc"

# Install conda environment
RUN conda create -n py39torch200 python=3.9 -y

RUN bash -c "source activate py39torch200 && conda install -c anaconda pandas h5py ipython pyyaml pylint pillow setuptools -y"
RUN bash -c "source activate py39torch200 && conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia -y"
RUN bash -c "source activate py39torch200 && conda install -c conda-forge matplotlib librosa pudb tqdm ruamel.yaml jupyterlab sox cupy jupyterlab onnxruntime protobuf tensorboard -y"
RUN bash -c "source activate py39torch200 && conda install -c omnia termcolor -y"
RUN bash -c "source activate py39torch200 && pip install pesq"
RUN bash -c "source activate py39torch200 && pip install pystoi"
RUN bash -c "source activate py39torch200 && pip install PySoundFile"
RUN bash -c "source activate py39torch200 && pip install gpustat"
RUN bash -c "source activate py39torch200 && pip install pysndfx"
RUN bash -c "source activate py39torch200 && pip install thop"
RUN bash -c "source activate py39torch200 && pip install torchstat"
RUN bash -c "source activate py39torch200 && pip install ptflops"
RUN bash -c "source activate py39torch200 && pip install webrtcvad"
RUN bash -c "source activate py39torch200 && pip install nnAudio"
RUN bash -c "source activate py39torch200 && pip install learn2learn"

RUN bash -c "conda clean --all"

