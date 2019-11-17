---
layout: post
title: Bài 3 - Audio - mic
author: Thong Ho
date: '2019-11-06 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/orangepi-bai3-audio-mic
---

## Test thử speaker trên orange pi zero
- Chạy 1 file mp3 :

```
root@orangepizero:~# aplay song.mp3
```

- Test speaker: 

```
mltech@orangepizero:~$ speaker-test

speaker-test 1.1.0

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 256 to 524288
Period size range from 128 to 65536
Using max buffer size 524288
Periods = 4
was set period_size = 65536
was set buffer_size = 524288
 0 - Front Left
Time per period = 2.759530
 0 - Front Left
Time per period = 2.769747
 0 - Front Left
Time per period = 2.769853
 0 - Front Left

```

- Điều chỉnh các thông số về loa và mic 

```
alsamixer

```

![](/assets/img/embedded_computer/orangepi/bai3_alsamixer.jpg)


## Test thử mic trên orange pi:
- Ghi âm 1 files trong vòng 10s. Nếu không muốn ghi chỉ 10s thì có thể bỏ phần * -d 10*

```
arecord -d 10 /tmp/test-mic.wav
```

- Chạy file ghi âm

```
aplay /tmp/test-mic.wav
```


## Tham khảo :
- project door phone [here](https://github.com/gravaigu/doorphone.git)