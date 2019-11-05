---
layout: post
title: Esp8266, MQTT and NodeRed
author: Thong Ho
date: '2019-11-02 20:55:23 +0530'
categories: iot
summary: Hướng dan esp mqtt  and nodeRed
thumbnail: kalman2.png
permalink: /:categories/esp-mqtt-nodered
use_math: true
---



## Kiến trúc  
- Kiến trúc hệ thống như hình : 
    ![](/assets/img/iot/mqtt.JPG)


## Chân vào ra :
- Bài hướng dẫn link [here](https://randomnerdtutorials.com/esp8266-pinout-reference-gpios/)

- Sơ đồ sử dụng chân: 
    ![](/assets/img/iot/esp_pin_notes.JPG)

## Cài đặt node-red

- Cài đặt các gói cho node red: 
    - Chọn Manage Palette
    - Search node-red-contrib-mqtt-broker
    - Click on Install Button

    - Node-Red Dashboard

## Cài đặt mqtt :
    - Tạo 1 instance trên cloudmqtt
    - tạo 1 user sử dụng ví dụ :
        ```
        smart4chanel_maithe

        ```


## Deploy with Heroku
- Tạo tài khoản heroku . Tham khảo [here](http://arduino.vn/tutorial/5777-lap-trinh-keo-tha-cho-cac-du-iot-su-dung-node-red-va-inut-platform)
- Download heroku cli [here](https://cli-assets.heroku.com/branches/stable/heroku-windows-amd64.exe)

- Tren màn hình terminal gõ :
    ```
    heroku create
    ```
- Up dữ liệu lên heroku server :
    ```
    git push heroku master
    ```

## Một số trang tham khảo :
- Hướng dẫn các bước từ cài đặt trên window đến lập trình esp bởi video [here](https://www.instructables.com/id/MQTTNODE-REDESP8266/)
- Hướng dẫn tiếng việt về tạo tài khoản cloudmqtt và esp [here](https://hocarm.org/mqtt-va-esp8266/)