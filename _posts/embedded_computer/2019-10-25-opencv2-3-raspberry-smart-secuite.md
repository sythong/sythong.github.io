---
layout: post
title: Hướng dẫn cài đặt opencv2,3 và hệ thống an ninh thông minh trên raspberry pi
author: Thong Ho
date: '2019-10-24 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/install-opencv3-raspberrypi-smart-security
---


## Hướng dẫn cài đăt:
Toàn bộ hướng dẫn theo link [here](https://www.youtube.com/watch?v=Y2QFu-tTvTI&t=491s)

## Cài đặt opencv2 hoặc opencv3 trên raspberry pi
link [here](https://www.pyimagesearch.com/2016/04/18/install-guide-raspberry-pi-3-raspbian-jessie-opencv-3/)
### bước 1. Mở rộng file bộ nhớ
- Thay đổi thông tin bộ nhớ trong file config

```
sudo raspi-config
```
- Kiểm tra bộ nhớ
```
df -h
```

### Bước 2: Cài đặt các thư viện phụ thuộc
- Cập nhật các gói :
```
sudo apt-get update
sudo apt-get upgrade
```
- Cài đặt Cmake (thời gian 40s)

```
sudo apt-get install build-essential cmake pkg-config
```

- Cài đặt các gói image I/O để load ảnh, video

```
sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev

sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libxvidcore-dev libx264-dev
```

- Cài đặt thư viện cho **highgui**

```
sudo apt-get install libgtk2.0-dev
```

- Cài đặt cá thư viện Matrix

```
sudo apt-get install libatlas-base-dev gfortran
```

- Cài đặt header files để compile OpenCV trên python 2.7 và python 3

### Tải gói OpenCV souce code và opencv_contrib
```
cd ~
wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.1.0.zip
unzip opencv.zip

$ wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.1.0.zip
$ unzip opencv_contrib.zip

```

## Bước 4: Cài đặt pip và cài đặt virtualenv

```
sudo pip install virtualenv virtualenvwrapper
sudo rm -rf ~/.cache/pip


# virtualenv and virtualenvwrapper
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3.7
export PROJECT_HOME=$HOME/Devel
source /usr/local/bin/virtualenvwrapper.sh


echo -e "\n# virtualenv and virtualenvwrapper" >> ~/.profile
echo "export WORKON_HOME=$HOME/.virtualenvs" >> ~/.profile
echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.profile

source ~/.profile

```
- Creating python virtual environment

```
# với opencv2
mkvirtualenv cv -p python2

# với opencv3
mkvirtualenv cv -p python3
```
- Kiểm tra virtual environment

```
source ~/.profile
workon cv
```

- Cài đặt numpy

```
pip install numpy
```

### Bước 5: Compile và cài đặt OpenCV
- chạy cv

```
workon cv
```

- CMake openCV

```
cd ~/opencv-3.1.0/
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.1.0/modules \
    -DENABLE_PRECOMPILED_HEADERS=OFF \
    -D BUILD_EXAMPLES=ON ..


make -j4  

```
- Sau khi hoàn thành :

```
sudo make install
sudo ldconfig
```

### Bước 6: Hoàn thành cài cài đặt openCV trên pi

- Đối với python 2.7: Nếu bạn cài thành cài đặt ở bước 5 không lỗi, kiểm tra cài đặt. sẽ thấy :

```
$ ls -l /usr/local/lib/python2.7/site-packages/
total 1852 -rw-r--r-- 1 root staff 1895772 Mar 20 20:00 cv2.so
```

- Bước cuối cùng:

```

cd ~/.virtualenvs/cv/lib/python2.7/site-packages/
ln -s /usr/local/lib/python2.7/site-packages/cv2.so cv2.so
```

- Đối với python 3: Sau khi chạy make install 

```
$ ls -l /usr/local/lib/python3.4/site-packages/
total 1852  -rw-r--r-- 1 root staff 1895932 Mar 20 21:51 cv2.cpython-34m.so
```

```
cd /usr/local/lib/python3.4/site-packages/
sudo mv cv2.cpython-34m.so cv2.so

cd ~/.virtualenvs/cv/lib/python3.4/site-packages/
ln -s /usr/local/lib/python3.4/site-packages/cv2.so cv2.so
```

### Bước 7: kiểm tra OpenCV3 

```
source ~/.profile 
workon cv
python
>>> import cv2
>>> cv2.__version__
'3.1.0'
>>>
$ source ~/.profile 
$ workon cv
$ python
>>> import cv2
>>> cv2.__version__
'3.1.0'
>>>
```



## Viết chương trình smart security camera:
link [here](https://github.com/HackerShackOfficial/Smart-Security-Camera)

