---
layout: post
title: Bai6 - Cài đặt camera và gvieets chuong trình thư viện io cho raspberry pi
author: Thong Ho
date: '2019-09-21 14:35:23 +0530'
categories: courses
summary:  Giới thiệu
thumbnail: siteleaf.jpg
permalink: /:categories/setup-camera-ras
---


## Cài đặt camera Raspberry pi

``` 
git clone https://github.com/cedricve/raspicam.git
cd raspicam
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig
```