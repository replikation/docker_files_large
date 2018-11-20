FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN git clone https://github.com/infphilo/centrifuge
WORKDIR /centrifuge
RUN make
RUN make install prefix=/usr/local
ENV PATH /centrifuge/:$PATH
# get the index database 
RUN DWNL=$(curl -s http://www.ccb.jhu.edu/software/centrifuge/ | grep "tar.gz" | tail -1 | cut -f2 -d'"')
RUN mkdir /centrifuge/database
WORKDIR /centrifuge/database
RUN wget $DWNL
RUN tar -xf /centrifuge/database/p_compressed_2018_4_15.tar.gz -C /centrifuge/database
RUN rm -f /centrifuge/database/p_compressed_*.tar.gz
