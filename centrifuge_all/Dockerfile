FROM replikation/debian_basic
MAINTAINER Christian Brandt <christian.jena@gmail.com>
RUN git clone https://github.com/infphilo/centrifuge
WORKDIR /centrifuge
RUN make
RUN make install prefix=/usr/local
ENV PATH /centrifuge/:$PATH
# get the index database
RUN mkdir /centrifuge/database
WORKDIR /centrifuge/database
RUN DWNL=$(curl -s http://www.ccb.jhu.edu/software/centrifuge/ | grep "p_compressed+h+v.tar.gz" | cut -f2 -d'"') && wget $DWNL
RUN /bin/bash -c "tar -xf /centrifuge/database/p_compressed*.tar.gz -C /centrifuge/database"
RUN /bin/bash -c "rm -f /centrifuge/database/p_compressed*.tar.gz"
# centrifuge-kreport needs ...help to find python
RUN ln -s -T /usr/bin/python3 /usr/bin/python
