FROM tensorflow/tensorflow:latest-gpu-py3

# Install Keras
RUN pip3 --no-cache-dir install keras

# Install image tools
RUN pip3 --no-cache-dir install tifffile

# Install Database tools
RUN pip3 --no-cache-dir install psycopg2 \
        sqlalchemy \
        asyncpg \
        peewee

# Upgrade numpy
RUN pip3 --no-cache-dir install --upgrade numpy
RUN pip3 --no-cache-dir install \
        Pillow \
        geopandas \
        shapely 
        # xgboost
        
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

# install mxnet
RUN pip3 --no-cache-dir install mxnet  && \
    pip3 --no-cache-dir install graphviz

# install pytorch
# RUN conda install pytorch torchvision -c soumith

# User permissions
RUN useradd ipynb && \
    mkdir /home/ipynb && chown -R ipynb:ipynb /home/ipynb && \
    mkdir /home/ipynb/.jupyter && cp /root/.jupyter/jupyter_notebook_config.py /home/ipynb/.jupyter/ && \
    chown -R ipynb:ipynb /notebooks

WORKDIR /notebooks

USER ipynb