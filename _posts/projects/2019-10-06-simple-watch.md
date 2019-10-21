---
layout: post
title: Simple Watch with Arduino
author: Thong Ho
date: '2019-10-06 07:35:23 +0530'
categories: projects
summary:  Hướng dẫn tạo đồng hồ đơn giản
thumbnail: siteleaf.jpg
permalink: /:categories/simple-watch
---


## Tóm tắt

## Thành phần - chuẩn bị
- Các thành phần cơ bản cho mạch như hình vẽ: 
![một số link kiên cơ bản](/assets/img/projects/1.simple-watch/thanhphan2.jpg)

    1. Mạch vi điều khiển chính dùng esp D1 [wifi d1](http://www.dientunhatrang.com/san-pham-p1270/d1-mini-v3-0-0-wifi-iot-4mb-tuong-thich-esp8266.html) 
    2. Màn hình oled 0.96 inch : [oled](http://www.dientunhatrang.com/san-pham-p1172/0-96-inch-oled-module-orangepi-6-chan.html)
    3. Mạch sạc và quản lý cell pin [link](http://www.dientunhatrang.com/san-pham-p1304/mach-tang-cuong-cho-pin-lithium-d1-mini.html)
    4. Pin lithium 3.7V 400maH  [here](https://shopee.vn/Pin-s%E1%BA%A1c-502040-400mah-i.3980731.1212267190?gclid=Cj0KCQjwoebsBRCHARIsAC3JP0KWDYhcWGDxbIoJEWpA2OqJlq6_FWZ2CSRFpOhJxW_m-SFtHIpRjWEaAvU5EALw_wcB)
    5. cảm biến nhiệt độ DS18b20 [link](http://www.dientunhatrang.com/san-pham-p1328/dau-do-cam-bien-nhiet-do-ds18b20-dai-1m.html)
    6. module đồng hồ thời gian thực ds1307 [here](http://www.dientunhatrang.com/san-pham-p1198/module-thoi-gian-thuc-rtc-ds1307.html)
    7. Mạch tự tích hợp toàn bộ hệ thống (Đang được vẽ mạch)

- sơ đồ mạch thiết kế cho đồng hồ : 
    ![sơ đô mạch](/assets/img/projects/1.simple-watch/sch_1.jpg)

    
