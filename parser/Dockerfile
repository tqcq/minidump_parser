FROM ubuntu:20.04

ENV PATH "$PATH:/work/depot_tools"

WORKDIR /work

# install base-tools
RUN apt-get update -y && \
    apt-get install -y git gcc g++ make wget

# setup depot_tools, fetch breakpad
RUN git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git depot_tools && \
    update_depot_tools && \
    fetch breakpad 

# compile tools and install
RUN cd src && \
    /bin/bash configure && \
    make install

COPY parse_dump /usr/local/bin
COPY parse_dump_dir /usr/local/bin

RUN chmod a+x /usr/local/bin/parse_dump*

# 
# /dump +
#       + aa.zip
#       + bb.zip
#       + skybox.apk
#

WORKDIR /dumpdir

CMD ["echo", "usage: auto_parse your_dump_dir"]
