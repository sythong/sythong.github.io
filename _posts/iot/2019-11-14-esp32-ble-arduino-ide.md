---
layout: post
title: Lập trình BLE cho ESP32 trên Arduino IDE
author: Thong Ho
date: '2019-11-13 20:55:23 +0530'
categories: iot
summary: Hướng dan esp và BLE
thumbnail: kalman2.png
permalink: /:categories/esp32-ble
use_math: true
---


## Giới thiệu
- Bluetooth Low Energy, BLE for short, is a power-conserving variant of Bluetooth. BLE ứng dụng trong khoảng cách truyền ngắn với một số lượng data bé (low bandwidth). Không giống như Bluetooth là luôn luôn mở (on), BLE chuyển về trạng thái sleep mode ngoại trừ khi kết nối được thiết lập. 
- So sánh BLE và Blutooth thông thường như hình ![comparing](/assets/img/iot/esp32/Bluetooth-vs-BLE.png)
- Due to its properties, BLE is suitable for applications that need to exchange small amounts of data periodically running on a coin cell. For example, BLE is of great use in healthcare, fitness, tracking, beacons, security, and home automation industries.


### Tham khảo các bài viết:
- Giới thiệu về ESP32 và các hướng dẫn [here](https://randomnerdtutorials.com/getting-started-with-esp32/)
- Hướng dẫn lập cài đặt lập trình arduino IDE cho esp32 tại [link](https://randomnerdtutorials.com/installing-the-esp32-board-in-arduino-ide-windows-instructions/)
- Hướng dẫn Bluetooth low energy kết nối với điện thoại tại [here](https://www.instructables.com/id/ESP32-Bluetooth-Low-Energy/)

- Hướng dẫn chính về BLE và esp32 [here](https://randomnerdtutorials.com/esp32-bluetooth-low-energy-ble-arduino-ide/)

## BLE Server và client
- Với BLE, có 2 kiểu thiết bị: server và client. ESP32 có thể hoặc là client hoặc là server

- The server quảng bá cái bản tin về sự tồn tại của nó, do đó các thiết bị khác có thể tìm thấy và đọc được nội dụng chứa trong data của bản tin đó. The client tìm kiếm các thiết bị xung quanh, và khi tìm thấy server nó mong muốn, nó sẽ thiết lập kết nối và lắng nghe các các dữ liệu gửi đến. Đó được gọi là point-to-point communication.
    ![server-client](/assets/img/iot/esp32/BLE-server-and-client.png)
- Như đã đề cập trước đó, BLE cũng hỗ trợ 2 chế độ là : broadcast và mesh network:
    - Broadcast mode: the server transmits data to many clients that are connected;
    - Mesh network: all the devices are connected, this is a many to many connection.
- Even though the broadcast and mesh network setups are possible to implement, they were developed very recently, so there aren’t many examples implemented for the ESP32 at this moment.

## GATT
- GATT stands for Generic Attributes and it defines an hierarchical data structure that is exposed to connected BLE devices. This means that GATT defines the way that two BLE devices send and receive standard messages. Understanding this hierarchy is important, because it will make it easier to understand how to use the BLE and write your applications.



## CODE VỚI ESP32
- Code thư viện ble mẫu cho esp32 tại [github](https://github.com/nkolban/ESP32_BLE_Arduino)