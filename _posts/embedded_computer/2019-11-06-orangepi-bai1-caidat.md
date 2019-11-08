---
layout: post
title: Bài 1 - Cấu hình orange pi
author: Thong Ho
date: '2019-11-06 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/orangepi-bai1-cauhinh
---

## Hướng dẫn cài đặt hệ điều hành 
### 1. chuẩn bị:
- Phần mềm SD Card Formatter để format các file trong thẻ nhớ (nếu thẻ đang có image linux)
- Phần mềm để read/write images vào thẻ nhớ (Etcher hoặc Win32DiskImager)
- Thẻ nhớ 16gb hoặc tùy bạn nên từ 4Gb trở lên
- hệ điều hành (images) tài từ trang chủ
- usb-com để debug giao tiếp với máy tính
- Phần mềm putty để remote qua uart

### 2. Khi bung hệ điều hành vào thẻ nhớ xong, đăng nhập:
- Cấu hình putty serial : baudrate (115200)


- Tài khoản :

```
    user name : root
    Pass: 1234
```

- Sau đó bạn nhập tên và mật khẩu mới

### 3. Cấu hình kết nối internet (wifi ) WLAN0:
1. Mở file /etc/network/interface 

```
sudo nano /etc/network/interfaces
```

2. cấu hình nội dung :

```cpp
auto wlan0
iface wlan0 inet dhcp
wpa-ssid <tên wifi>
wpa-psk <mật khẩu>
```

3. lưu file *CTR + O*

4. Thoát *CTR + X*

5. cập nhật kết nối bằng lệnh dưới hoặc reboot

```cpp
sudo ifup wlan0
```

- Kiểm tra kết nối bằng lệnh

```
ifconfig
```


