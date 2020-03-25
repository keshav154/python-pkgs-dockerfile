FROM 036136800740.dkr.ecr.us-west-2.amazonaws.com/vocareum:jupyter-python
RUN apt -y update && apt -y install cmake libopenblas-dev ca-certificates caffe-cpu libcairo2-dev \
libdbus-1-3 libdbus-1-dev  expat freeglut3 freeglut3-dev libglew-dev mesa-utils python-pyfribidi libgtk-3-dev \
libgflags-dev giflib-tools gobject-introspection gstreamer1.0-plugins-bad gstreamer1.0-libav libharfbuzz-dev \
libjbig-dev libjpeg-dev lame libblas-dev libboost-all-dev libatlas-base-dev libcurl4 libcurl4-openssl-dev \
libedit-dev libffi-dev libgcc-7-dev gfortran libglu1-mesa libxi-dev libxmu-dev libglu1-mesa-dev libblas-dev liblapack-dev \
liblapacke libopenblas-base libopus-dev libpng-dev libprotobuf-dev libsodium-dev libssh2-1 autoconf libwebp-dev \
libxcb-render0-dev libxml2 libxslt-dev python-lzo libmpc-dev libncurses-dev libopenblas-dev openjdk-8-jdk \
openmpi-bin libssl-dev libffi-dev libpango-1.0-0 patchelf libpixman-1-dev libpthread-stubs0-dev unixodbc-dev \
x264 xserver-xorg-dev libxext-dev libxinerama-dev libxrandr-dev libxi-dev libudev-dev xorg-server-source \
xz-utils zlib1g-dev bwidget ca-certificates r-cran-abind r-cran-assertthat r-base r-cran-base64enc r-cran-bindrcpp \
libasound2 alsa libdb-dev flac binutils-common fontconfig
RUN apt update 
RUN cd /tmp \
&& wget https://repo.continuum.io/pkgs/main/linux-64/_ipyw_jlab_nb_ext_conf-0.1.0-py37_0.tar.bz2 \
&& tar xvf _ipyw_jlab_nb_ext_conf-0.1.0-py37_0.tar.bz2 \
&& cd info && cd recipe \
&& bash build.sh 
RUN cd /tmp && wget https://c-ares.haxx.se/download/c-ares-1.16.0.tar.gz && tar xvf c-ares-1.16.0.tar.gz && cd c-ares-1.16.0 && bash configure && make && make install 
RUN cd /tmp && git clone https://github.com/conda/conda-verify.git && cd conda-verify && python3.7 setup.py install 
RUN cd /tmp && curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash - && sudo apt-get install -y nodejs 
RUN cd /tmp && sudo apt-get install -y nodejs-dev node-gyp libssl1.0-dev && apt-get -y install npm && npm install -g configurable-http-proxy 
RUN cd /tmp && git clone https://github.com/NSLS-II/databroker-browser.git && cd databroker-browser && python3.7 setup.py install 
RUN cd /tmp && sudo apt -y install libdbus-1-3 libdbus-1-dev && pip3.7 install dbus-python 
RUN apt install -y cmake && cd /tmp && git clone https://github.com/Theano/libgpuarray.git && cd libgpuarray && mkdir Build && cd Build && cmake .. -DCMAKE_BUILD_TYPE=Release && make && make install 
RUN cd /tmp && wget https://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.16.tar.gz && tar xvf libiconv-1.16.tar.gz  && cd libiconv-1.16 && ./configure --prefix=/usr/local && make && make install

RUN cd /tmp && wget http://lvserver.ugent.be/xraylib/xraylib-3.3.0.tar.gz && gunzip xraylib-3.3.0.tar.gz && tar xvf xraylib-3.3.0.tar && cd xraylib-3.3.0 && ./configure && make && make install
RUN cd /tmp && git clone https://github.com/nbro/tktable.git && cd tktable && python3.7 setup.py install 
# RUN cd /tmp && wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.1.85-1_amd64.deb 
# RUN apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub 
#UN cd /tmp && wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.1.85-1_amd64.deb && dpkg -i cuda-repo-ubuntu1604_9.1.85-1_amd64.deb 
#RUN  apt update 
#RUN  apt-get install -y cuda-9.1 
RUN cd /tmp && git clone https://github.com/gypified/libogg.git && cd libogg && ./configure && make && make install 
RUN cd /tmp && wget http://portaudio.com/archives/pa_stable_v190600_20161030.tgz && tar xvf pa_stable_v190600_20161030.tgz && cd portaudio && ./configure && make && make install 
RUN apt-get install -y autoconf && cd /tmp && git clone https://github.com/yasm/yasm.git && cd yasm && ./autogen.sh && make && make install
RUN cd /tmp && git clone https://chromium.googlesource.com/webm/libvpx && cd libvpx && ./configure && make && make install 
RUN cd /tmp && wget https://ftp.gnu.org/gnu/nettle/nettle-3.5.tar.gz && tar xvf nettle-3.5.tar.gz && cd nettle-3.5 && ./configure && make && make install 
RUN cd /tmp && git clone git://sourceware.org/git/bzip2.git && cd bzip2 && make && make install
RUN cd /tmp apt -y install libdbus-1-3 libdbus-1-dev && pip3.7 install dbus-python
RUN cd /tmp && wget https://download.savannah.gnu.org/releases/freetype/freetype-2.10.0.tar.gz && tar xvf freetype-2.10.0.tar.gz && cd freetype-2.10.0 && ./configure && make && make install
RUN apt install -y libglib2.0-dev giflib-tools libgraphite2-3 libgraphite2-utils gtk2.0 libhdf5-serial-dev python3-jupyter-client krb5-user libedit-dev  libxcb-render0-dev 
RUN python3.7 -m nltk.downloader -d /usr/local/share/nltk_data all 
RUN cd /tmp && cd libgpuarray && python3.7 setup.py install
RUN pip3.7 install torch==1.3.1+cpu torchvision==0.4.2+cpu -f https://download.pytorch.org/whl/torch_stable.html
RUN pip3.7 install --upgrade pip
WORKDIR /tmp
COPY . .
RUN pip3.7 install -r delta.txt
