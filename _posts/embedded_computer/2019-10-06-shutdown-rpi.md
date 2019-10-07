---
layout: post
title: Tạo nút tắt máy tính nhúng raspberry pi
author: Thong Ho
date: '2019-10-2 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn tắt nguồn máy tính nhúng từ nút nhấn
thumbnail: siteleaf.jpg
permalink: /:categories/shutdown-rpi
---

## Tại sao cần có nút nhấn tắt nguồn cho pi
- Như chúng ta biết thì hệ điều hành của pi được nằm trên thẻ nhớ. Khi bạn tạo các ứng dụng cho raspberry pi, khởi động lên có thể sẽ chỉ chạy vào mỗi chương trình của bạn. do đó nếu tắt nguồn pi bằng cách rút nguồn đột ngột rất dễ gây ra hỏng thẻ nhớ. 

link tham khảo tiếng anh: [here](https://howchoo.com/g/mwnlytk3zmm/how-to-add-a-power-button-to-your-raspberry-pi)

## Xây dựng chương trình function cho tắt pi
- bạn có thể download trực tiếp chương trình từ link:
    ```
    git clone https://github.com/Howchoo/pi-power-button.git

    ./pi-power-button/script/install

    ```

- Chương trình có thể được viết bằng tay bằng ngôn ngữ python bằng chương trình sau:
    - Tạo 1 file python:
    ```
        sudo nano listen-for-shutdown.py
    ```
    - Copy đoạn code này vào vào nhấn CTR-X và Y để lưu lại :
    ```python
        #!/usr/bin/env python

        import RPi.GPIO as GPIO
        import subprocess


        GPIO.setmode(GPIO.BCM)
        GPIO.setup(3, GPIO.IN, pull_up_down=GPIO.PUD_UP)
        GPIO.wait_for_edge(3, GPIO.FALLING)

        subprocess.call(['shutdown', '-h', 'now'], shell=False)
    ```
- Bước tiếp theo là cần đưa chương trình này khởi động khi chúng ta khởi động raspi.
    -  di chuyển chương trình vào thư mục /usr/local/bin
    - Chmod cho chương trình ở chế độ thực thi (execuable)
    ```
    sudo mv listen-for-shutdown.py /usr/local/bin/
    sudo chmod +x /usr/local/bin/listen-for-shutdown.py
    ```
- Viết 1 đoạn code shell để start/stop chương trình trên. 
    - Tạo chương file .sh:

    ```
    sudo nano listen-for-shutdown.sh
    ```
    - Thêm đoạn code bên dưới và lưu lại:

    ```
    #! /bin/sh

    ### BEGIN INIT INFO
    # Provides:          listen-for-shutdown.py
    # Required-Start:    $remote_fs $syslog
    # Required-Stop:     $remote_fs $syslog
    # Default-Start:     2 3 4 5
    # Default-Stop:      0 1 6
    ### END INIT INFO

    # If you want a command to always run, put it here

    # Carry out specific functions when asked to by the system
    case "$1" in
    start)
        echo "Starting listen-for-shutdown.py"
        /usr/local/bin/listen-for-shutdown.py &
        ;;
    stop)
        echo "Stopping listen-for-shutdown.py"
        pkill -f /usr/local/bin/listen-for-shutdown.py
        ;;
    *)
        echo 
        exit 1
        ;;
    esac

    exit 0

    ```

    - Di chuyển vào thư mục /etc/init.d  và cho phép chương trình execuable
    ```
        sudo mv listen-for-shutdown.sh /etc/init.d/
        sudo chmod +x /etc/init.d/listen-for-shutdown.sh
    ```
    
    - Đăng ký dịch vụ cho đoạn script khởi động:
    ```
        sudo update-rc.d listen-for-shutdown.sh defaults
    ```

    - Start script :
    ```
        sudo /etc/init.d/listen-for-shutdown.sh start
    ```

- OK, Done, let's enjoy.