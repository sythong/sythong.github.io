---
layout: post
title: Hướng dẫn cài đặt opencv4 cho raspberry pi
author: Thong Ho
date: '2019-10-24 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/install-opencv4-raspberrypi
---



## Cài đặt open CV 4 cho raspberry pi
- Một số lệnh để gỡ các ứng dụng không cần thiết trên pi và cài đặt opencv

```cpp

sudo apt-get purge wolfram-engine
sudo apt-get purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove


sudo raspi-config

sudo reboot
df -h

///////////update raspberry pi3
sudo apt-get upgrade
sudo apt-get update

sudo nano /etc/dphys-swapfile
#set this value CONF_SWAPSIZE=2048

 sudo /etc/init.d/dphys-swapfile stop
 sudo /etc/init.d/dphys-swapfile start

```

## Clone openCV từ github
- Kiểm tra bộ nhớ của trong sdcard
```
df
```


```
#install prerequisite
[compiler]     sudo apt-get install build-essential cmake pkg-config                                               //developer package
               sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
               sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
               sudo apt-get install libxvidcore-dev libx264-dev

[required]     sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
[optional]     sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

               sudo apt-get install libgtk2.0-dev libgtk-3-dev                                                     // gui of open cv   gtk package
               sudo apt-get install libatlas-base-dev gfortran                                                     // matrix function


#create opencv directory and clone opencv and opencv_contrib
mkdir opencv
cd ~/opencv
git clone https://github.com/opencv/opencv.git
git clone https://github.com/opencv/opencv_contrib.git

#create build directory
mkdir build
cd build


////////////////////create make file using CMAKE (observe verbose, here you can find path for openCV install directories)
cmake -D CMAKE_BUILD_TYPE=Release -DCMAKE_EXTRA_MODULES_PATH=../opencv_contrib/modules/ -D CMAKE_INSTALL_PREFIX=/usr/local ../opencv -DBUILD_opencv_java=OFF -DBUILD_opencv_python2=OFF -DBUILD_opencv_python3=OFF

make -j4
sudo make install

sudo ldconfig

sudo nano /etc/dphys-swapfile
//////////set this value CONF_SWAPSIZE=100

 sudo /etc/init.d/dphys-swapfile stop
 sudo /etc/init.d/dphys-swapfile start

```

```
sudo nano /etc/ld.so.conf.d/opencv.conf

/usr/local/lib                        //  add  this path


sudo ldconfig


sudo nano /etc/bash.bashrc

PKG_CONFIG PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig               // add this path

export PKG_CONFIG_PATH

```

```
geany open cv path for build
g++ $(pkg-config opencv4 --cflags --libs) -o %e %f



geany open cv path for build
g++ $(pkg-config opencv4 --cflags --libs) -o %e %f



installing raspicam

git clone https://github.com/cedricve/raspicam.git
cd raspicam
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig

```


```
sudo nano /etc/ld.so.conf.d/opencv.conf

/usr/local/lib                        //  add  this path

sudo ldconfig


sudo nano /etc/bash.bashrc

PKG_CONFIG PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig               // add this path

export PKG_CONFIG_PATH
```



# Cài đặt trên window 
- link hướng dẫn [here](https://pysource.com/2019/03/15/how-to-install-python-3-and-opencv-4-on-windows/)
- Link download [here](https://www.lfd.uci.edu/~gohlke/pythonlibs/#opencv)

- Cài đặt 
```
python pip -m install opencv_python‑4.0.1+contrib‑cp37‑cp36m‑win_amd64.whl
```
- Cài đặt numpy
```
python pip -m install numpy
```