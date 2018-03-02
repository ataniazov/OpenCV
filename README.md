# OpenCV
OpenCV Projects

## Install

### Installing OpenCV 3.4.1 on Ubuntu 16.04.4

```bash
sudo apt install build-essential 
sudo apt install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
```

#### To install opencv by building from source:

The steps needed to be taken in order to install OpenCV 3.4.1 are:

1. Update and Upgrade and Cleanup (Required for error-free installation)
2. Install Dependencies
3. Download and Build OpenCV

Update and Upgrade and Cleanup (Required for error-free installation)

```bash
sudo apt update && sudo apt dist-upgrade && sudo apt autoremove
```

Now that we have the updates ready, we are ready to install dependencies.

#### Install Dependencies

```bash
sudo apt install build-essential cmake git pkg-config unzip
sudo apt install libgtk2.0-dev libavcodec-dev libavformat-dev libswscale-dev
```

The following command is needed to process images:

```bash
sudo apt install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
```

To process videos:

```bash
sudo apt install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt install libxvidcore-dev libx264-dev
```

For GUI:

```bash
sudo apt install libgtk-3-dev
```

For optimization:

```bash
sudo apt install libatlas-base-dev gfortran pylint
```

To build OpenCV binding for python 3.

```bash
sudo apt install python3.5-dev python3-numpy libtbb2 libtbb-dev
```

Other:

```bash
sudo apt install libtiff5-dev libeigen3-dev libtheora-dev libvorbis-dev   sphinx-common yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libopenexr-dev libgstreamer-plugins-base1.0-dev libavutil-dev libavfilter-dev libavresample-dev
```

We are now ready to download and build OpenCV on our Ubuntu machine.

#### Install Dependencies

Download with wget:

```bash
cd ~/Downloads/

wget -O opencv.zip https://github.com/opencv/opencv/archive/3.4.1.zip
unzip opencv.zip

wget -O opencv-contrib.zip https://github.com/opencv/opencv_contrib/archive/3.4.1.zip
unzip opencv-contrib.zip
```

Or clone with git:

```bash
git clone https://github.com/opencv/opencv.git
cd opencv/
git checkout 3.4.1 
cd ..

git clone https://github.com/opencv/opencv_contrib.git
cd opencv_contrib/
git checkout 3.4.1
cd ..
```

#### Build and Install OpenCV

```bash

mkdir ~/.local/bin/
cd opencv/
mkdir build
cd build

cmake -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D ENABLE_AVX=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=OFF -D WITH_V4L=OFF -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=~/.local/ -D OPENCV_EXTRA_MODULES_PATH=~../../opencv_contrib/modules ../../opencv/

make -j4
 
make install
 
ldconfig
 
exit
 
cd ~
```

#### env

```bash
export PKG_CONFIG_PATH=${HOME}/.local/lib/pkgconfig
export LD_LIBRARY_PATH=${HOME}/.local/lib/:${LD_LIBRARY_PATH}
```