FROM jupyter/tensorflow-notebook

# Upgrade pip
RUN pip3 --no-cache-dir install --upgrade pip

# Install Keras
RUN pip --no-cache-dir install keras

# Install image tools
RUN pip --no-cache-dir install tifffile

# Install Database tools
RUN pip --no-cache-dir install psycopg2-binary \
        sqlalchemy \
        asyncpg \
        peewee

# Upgrade numpy
RUN pip --no-cache-dir install --upgrade numpy
RUN pip --no-cache-dir install \
        Pillow \
        xgboost \
        geopandas \
        shapely 

# install mxnet
RUN pip --no-cache-dir install mxnet  && \
    pip --no-cache-dir install graphviz

# install pytorch
RUN conda install pytorch torchvision -c soumith