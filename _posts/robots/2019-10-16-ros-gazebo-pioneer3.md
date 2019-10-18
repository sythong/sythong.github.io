---
layout: post
title: Run ROS + gazebo voi pioneer 3
author: Thong Ho
date: '2019-10-16 20:55:23 +0530'
categories: Ros-and-Robot
summary: Hướng dẫn kết nối với ros
thumbnail: kalman2.png
permalink: /:categories/ros-gazebo-pioneer
use_math: true
---

## Hướng dẫn cài đặt packages cho mô phỏng gazebo của pioneer 3
- Link  [here](http://wiki.lofarolabs.com/index.php/Moving_The_Pioneer_3-DX_In_Gazebo)

```
$ cd <catkin_ws>/src
$ git clone https://github.com/SD-Robot-Vision/PioneerModel.git
$ cd ..
$ catkin_make

```

### Cài đặt gói điều khiển controllers 
```

```

## Sử dụng image ubiqutyrobotics 
- Cài đặt trên ubuntu mate trên raspberry pi từ wen ubiquity 
- Đăng nhập vào mật khẩu wifi được phát ra từ board 
```
robotseverywhere
```
- Sử dụng SSH :
```
ssh ubuntu@10.42.0.1
// pass
ubuntu
// da thay doi 123456789
```
- Tắt tính năng có sẵn của image:
```
    sudo systemctl disable magnibase

    
```