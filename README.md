COLMAP
======

Build from Source for Linux
-----

Shoudn't install COLMAP from ```apt-get```

Recommended dependencies: CUDA (at least version 7.X)
Dependencies from the default Ubuntu repositories:
```
sudo apt-get install \
    git \
    cmake \
    build-essential \
    libboost-program-options-dev \
    libboost-filesystem-dev \
    libboost-graph-dev \
    libboost-regex-dev \
    libboost-system-dev \
    libboost-test-dev \
    libeigen3-dev \
    libsuitesparse-dev \
    libfreeimage-dev \
    libgoogle-glog-dev \
    libgflags-dev \
    libglew-dev \
    qtbase5-dev \
    libqt5opengl5-dev \
    libcgal-dev
```


Under Ubuntu 16.04/18.04 the CMake configuration scripts of CGAL are broken and you must also install the CGAL Qt5 package:
```
sudo apt-get install libcgal-qt5-dev
```


Install Ceres Solver:
```
sudo apt-get install libatlas-base-dev libsuitesparse-dev
git clone https://ceres-solver.googlesource.com/ceres-solver
cd ceres-solver
git checkout $(git describe --tags) # Checkout the latest release
mkdir build
cd build
cmake .. -DBUILD_TESTING=OFF -DBUILD_EXAMPLES=OFF
make -j 1 #int vary on CPU cores
sudo make install
```


Configure and compile COLMAP:
```
git clone https://github.com/colmap/colmap.git
cd colmap
git checkout dev
mkdir build
cd build
cmake ..
make -j 1 #int vary on CPU cores, beware ran out of memory
sudo make install
```


Under newer Ubuntu versions it might be necessary to explicitly select the used GCC version due to compatiblity issues with CUDA, which can be done as:
```
CC=/usr/bin/gcc-6 CXX=/usr/bin/g++-6 cmake ..
```


Run COLMAP:
```
colmap -h
colmap gui
```


Documentation
-------------

The documentation is available at https://colmap.github.io/.


License
-------

The COLMAP library is licensed under the new BSD license. Note that this text
refers only to the license for COLMAP itself, independent of its dependencies,
which are separately licensed. Building COLMAP with these dependencies may
affect the resulting COLMAP license.

    Copyright (c) 2018, ETH Zurich and UNC Chapel Hill.
    All rights reserved.

    Redistribution and use in source and binary forms, with or without
    modification, are permitted provided that the following conditions are met:

        * Redistributions of source code must retain the above copyright
          notice, this list of conditions and the following disclaimer.

        * Redistributions in binary form must reproduce the above copyright
          notice, this list of conditions and the following disclaimer in the
          documentation and/or other materials provided with the distribution.

        * Neither the name of ETH Zurich and UNC Chapel Hill nor the names of
          its contributors may be used to endorse or promote products derived
          from this software without specific prior written permission.

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
    AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
    IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
    ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDERS OR CONTRIBUTORS BE
    LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
    CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
    SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
    INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
    CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
    ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
    POSSIBILITY OF SUCH DAMAGE.

    Author: Johannes L. Schoenberger (jsch-at-demuc-dot-de)
