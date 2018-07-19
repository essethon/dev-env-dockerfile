FROM tensorflow/tensorflow:latest-py3

# Upgrade pip
RUN pip --no-cache-dir install --upgrade pip

# Install Keras
RUN pip --no-cache-dir install keras

# Install image tools
RUN apt-get update && apt-get --fix-missing install -y \
    libsm6 libxext6 libfontconfig1 libxrender1 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN pip3 --no-cache-dir install tifffile opencv-python

# Install Database tools
RUN pip --no-cache-dir install psycopg2-binary \
        sqlalchemy \
        asyncpg \
        peewee

# Upgrade numpy
RUN pip3 --no-cache-dir install --upgrade numpy
RUN pip3 --no-cache-dir install \
        Pillow \
        geopandas \
        shapely \
        seaborn \
        pyecharts
        # xgboost

# build and install xgboost
RUN apt-get update && apt-get --fix-missing install -y git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
WORKDIR /opt
RUN git clone --recursive https://github.com/dmlc/xgboost.git
WORKDIR /opt/xgboost
RUN /opt/xgboost/build.sh && \
    pip3 --no-cache-dir install -e python-package
        
# install mapnik ，note: mapnik must install before gdal
RUN apt-get update && apt-get --fix-missing install -y python3-mapnik && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# install gdal  
RUN add-apt-repository -y ppa:ubuntugis/ppa && \ 
    apt-get update && \ 
    apt-get install -y --no-install-recommends gdal-bin libgdal-dev python3-gdal && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# install mxnet tflearn tqdm
RUN pip3 --no-cache-dir install mxnet graphviz tflearn tqdm

# install pytorch
# RUN conda install pytorch torchvision -c soumith

# install VIM
RUN apt-get update && apt-get --fix-missing install -y vim
RUN mkdir -p /root/.pip
COPY pip.conf /root/.pip/

# User permissions
# RUN useradd ipynb && \
#     mkdir /home/ipynb && \
#     mkdir /home/ipynb/.jupyter && cp /root/.jupyter/jupyter_notebook_config.py /home/ipynb/.jupyter/ && \
#     chown -R ipynb:ipynb /home/ipynb && \
#     chown -R ipynb:ipynb /notebooks

WORKDIR /notebooks

# USER ipynb