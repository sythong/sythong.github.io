---
layout: post
title: Bài 3 - Auido - mic
author: Thong Ho
date: '2019-11-06 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/orangepi-bai3-audio-mic
---

## Hướng dẫn lập trình GPIO với Orange pi
- Bài hướng dẫn chi tiết tại [here](https://opi-gpio.readthedocs.io/en/latest/install.html)

## Cài đặt
- Cài đặt thư viện OPi-gpio cho python 2.7 hoặc 3.x

```
sudo pip install --upgrade OPi.GPIO
```

- Nếu trường hợp chưa cài đặt pip sử dụng lệnh sau:

```
sudo apt install python3-pip   

hoặc cho 2.7
sudo apt install python-pip   
```

- Trường hợp pi của bạn bị báo lock như hình :

```
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
```

- Thì xử lý bằng cách :

```
    sudo rm /var/lib/apt/lists/lock
    sudo rm /var/cache/apt/archives/lock
    sudo rm /var/lib/dpkg/lock

    sudo dpkg --configure -a
    sudo apt install -f

```


