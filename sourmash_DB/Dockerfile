FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN apt-get update
RUN apt-get install -y python-dev python-tk
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py
RUN pip install numpy
RUN pip install scipy
RUN pip install matplotlib
RUN sed -i 's/tkagg/agg/g' /usr/local/lib/python2.7/dist-packages/matplotlib/mpl-data/matplotlibrc
RUN mkdir /root/.config/
RUN mkdir /root/.config/matplotlib
RUN pip install sourmash
RUN /bin/sh -c "echo 'backend: Agg' > /root/.config/matplotlib/matplotlibrc"
RUN mkdir /sourmash_DB
RUN wget https://s3-us-west-2.amazonaws.com/sourmash-databases/2018-03-29/genbank-d2-k31.tar.gz
RUN /bin/bash -c "tar -xf genbank-d2-k31.tar.gz -C /sourmash_DB/"
RUN rm -f genbank-d2-k31.tar.gz
ENV DB /sourmash_DB/genbank-k31.sbt.json
