FROM centos:6

#Configure repositories
RUN yum -y install wget centos-release-scl && \
    rpm --import 'http://linuxsoft.cern.ch/cern/slc68/x86_64/RPM-GPG-KEY-cern' && \
    wget -O '/etc/yum.repos.d/slc6-devtoolset.repo' 'http://linuxsoft.cern.ch/cern/devtoolset/slc6-devtoolset.repo'

RUN yum -y install \
    devtoolset-2-toolchain \
    devtoolset-8-toolchain

#Boost.Build
RUN wget https://github.com/boostorg/build/archive/boost-1.67.0.tar.gz && \
    tar -xzf boost-1.67.0.tar.gz && cd build-boost-1.67.0 && \
    source /opt/rh/devtoolset-2/enable && ./bootstrap.sh && ./b2 install --prefix=/usr/local && \
    rm -f ../boost-1.67.0.tar.gz && rm -rf ../build-boost-1.67.0

#cmake
RUN wget https://github.com/Kitware/CMake/releases/download/v3.15.3/cmake-3.15.3.tar.gz && \
    tar xzf cmake-3.15.3.tar.gz && cd cmake-3.15.3 && \
    source /opt/rh/devtoolset-2/enable && ./bootstrap --prefix=/usr/local && make && make install && \
    rm -f ../cmake-3.15.3.tar.gz && rm -rf ../cmake-3.15.3

#ninja
RUN wget https://github.com/ninja-build/ninja/archive/v1.9.0.tar.gz && \
    tar xzf v1.9.0.tar.gz && cd ninja-1.9.0 && \
    source /opt/rh/devtoolset-2/enable && ./configure.py --bootstrap && mv ninja /usr/local/bin/ && \
    rm -f ../v1.9.0.tar.gz && rm -rf ../ninja-1.9.0

