FROM tensorflow/tensorflow:latest-devel-gpu-py3

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
        xgboost \
        geopandas \
        shapely 

# install mxnet
RUN pip3 --no-cache-dir install mxnet  && \
    pip3 --no-cache-dir install graphviz

# install pytorch
RUN conda install pytorch torchvision -c soumith