---
layout: post
title: Bài 2 - Lập trình GPIO cho orange pi
author: Thong Ho
date: '2019-11-06 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/orangepi-bai2-gpio
---

## Hướng dẫn lập trình GPIO với Orange pi
- Bài hướng dẫn chi tiết tại [here](https://opi-gpio.readthedocs.io/en/latest/install.html)

## Sơ đồ chân 
- sơ đồ chân của orange pi
    ![](/assets/img/embedded_computer/orangepi/bia2_pinout.jpg)

- Sơ đồ chân của board đấu nối in - out mẫu:
    ![](/assets/img/embedded_computer/orangepi/mypinout.jpg)

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



##  Lập trình với python
1. cài đặt thư viện cần thiết cho python

```
sudo apt-get install python-dev
```
2. Tải thư viện về:

```python
    git clone https://github.com/duxingkei33/orangepi_PC_gpio_pyH3
    cd orangepi_PC_gpio_pyH3
    python setup.py install
```
3. Test code in example
- hoặc in my case :

    ```python
    #!/usr/bin/env python
    """Basic blinking led example.
    
    """
    
    import os
    import sys
    
    if not os.getegid() == 0:
    sys.exit('Script must be run as root')
    
    
    from time import sleep
    from pyA20.gpio import gpio
    from pyA20.gpio import port
    
    led = port.PA12
    led1 = port.PA11
    led2 = port.PA6
    
    gpio.init()
    gpio.setcfg(led, gpio.OUTPUT)
    gpio.setcfg(led1, gpio.OUTPUT)
    gpio.setcfg(led2, gpio.OUTPUT)
    
    try:
        print ("Press CTRL+C to exit")
        while True:
            gpio.output(led, 1)
            sleep(0.1)
            gpio.output(led, 0)
            sleep(0.6)
    
            gpio.output(led1, 1)
            sleep(0.1)
            gpio.output(led1, 0)
            sleep(0.6)
    
            gpio.output(led2, 1)
            sleep(0.1)
            gpio.output(led2, 0)
            sleep(0.6)
    
    except KeyboardInterrupt:
        print ("Goodbye.")

    ```


## Lập trình với c dùng wiringPi :
1. Tải thư viện mới nhất của WiringPi

```
sudo apt-get install git gcc make
```

- down thư viện từ [www.orangepi.org](www.orangepi.org) hoặc từ for orange pi iot[github](https://github.com/xpertsavenue/WiringOP-Zero)
    
    ```
    git clone https://github.com/xpertsavenue/WiringOP-Zero
    ```

2. Compile và cài đặt Wiring Pi:
- Làm theo hướng dẫn trên git

```
  cd WiringPi
  sudo ./build OrangePi_ZERO
  sudo ./build OrangePi_ZERO instal
```

3. Test Wiringpi với gpio command:
- Sử dụng lệnh :

```
gpio readall
```
![](/assets/img/embedded_computer/orangepi/bai2_readall.jpg)

- Use "gpio export pin mode" to explore wiringPi GPIO to the directory of /sys/class/gpio and set the GPIO mode into mode.:
![](/assets/img/embedded_computer/orangepi/bai2_exportpin.jpg)

- Use "gpio unexport pin" to cancel explore pin to /sys/class/gpio. For example:
![](/assets/img/embedded_computer/orangepi/bai2_unexportpin.jpg)

- Use "gpio exports" to check the current explored gpio. For expample:
orangepi# gpio exports
![](/assets/img/embedded_computer/orangepi/bai2_checkexportpin.jpg)

- Use "gpio mode pin mode" command to configure wiringPi pin mode. For example:
    - Configure pin wiringPi 25 as output mode
        
        ```
        orangepi# gpio mode 25 out
        ```
    - Configure pin wiringPi 26 as input mode

        ```
        orangepi# gpio mode 26 in
        ```

- Use "gpio write pin value" to write value of output mode pin, for example:
    - Configure pin wiringPi 25 as output pin：

        ``` 
       orangepi# gpio mode 25 out
       ```

    - Write 0 on wiringPi 25
        
        ``` 
        orangepi# gpio write 25 0
        ```

    - Write 1 wiringPi 25

        ```
        orangepi# gpio write 25 1
        ```

### Test code vs wiringpi: 
- Test output board

    ```cpp
    #include <stdio.h>
    #include <wiringPi.h>

    // LED Pin - wiringPi pin 0 is BCM_GPIO 17.

    #define	LED	0
    #define OUT8 	9
    #define OUT7	7
    #define OUT6	15
    #define OUT5	16
    #define OUT4	0
    #define OUT3	1
    #define OUT2	2
    #define OUT1	3

    int main (void)
    {
    printf ("Raspberry Pi blink\n") ;

    wiringPiSetup () ;
    pinMode (LED, OUTPUT) ;
    pinMode (OUT8, OUTPUT);
    pinMode (OUT7, OUTPUT);
    pinMode (OUT6, OUTPUT);
    pinMode (OUT5, OUTPUT);
    pinMode (OUT4, OUTPUT);
    pinMode (OUT3, OUTPUT);
    pinMode (OUT2, OUTPUT);
        pinMode (OUT1, OUTPUT);

    for (;;)
    {
        digitalWrite (LED, HIGH) ;	// On
        digitalWrite (OUT1, HIGH) ;	// On
        digitalWrite (OUT2, HIGH) ;	// On
        digitalWrite (OUT3, HIGH) ;	// On
        digitalWrite (OUT4, LOW) ;	// On
        digitalWrite (OUT5, LOW) ;	// On
        digitalWrite (OUT6, LOW) ;	// On
        digitalWrite (OUT7, LOW) ;	// On
        digitalWrite (OUT8, HIGH) ;	// On
        delay (500) ;		// mS
        digitalWrite (LED, LOW) ;	// Off
        digitalWrite (OUT1, LOW) ;	// On
        digitalWrite (OUT2, LOW) ;	// On
        digitalWrite (OUT3, LOW) ;	// On
        digitalWrite (OUT4, HIGH) ;	// On
        digitalWrite (OUT5, HIGH) ;	// On
        digitalWrite (OUT6, HIGH) ;	// On
        digitalWrite (OUT7, HIGH) ;	// On
        digitalWrite (OUT8, LOW) ;	// On
        delay (500) ;
    }
    return 0 ;
    }
    ```