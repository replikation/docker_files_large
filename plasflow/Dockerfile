FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
# install conda
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -b -p /conda
RUN rm -f Miniconda3-latest-Linux-x86_64.sh
ENV PATH /conda/bin:$PATH
# install plasflow
RUN conda config --add channels bioconda
RUN conda config --add channels conda-forge
RUN conda install plasflow -c smaegol
RUN conda install -c bioconda perl-bioperl perl-getopt-long
# modify shebangs for bioperl
RUN sed -i '1i#!/conda/bin/perl' /conda/bin/filter_sequences_by_length.pl
