---
layout: post
title: Lập trình Observer Design pattern trên Arduino
author: Thong Ho
date: '2019-11-16 11:55:23 +0530'
categories: embbed_programming
summary: this blog for learing and sharing knowledge
thumbnail: kalman2.png
permalink: /:categories/arduino-observer-pattern-design
use_math: true
---

## Giới thiệu: 
- Thông thường trong lập trình nhúng thì chúng ta thường chia nhỏ các công việc ra để dễ quản lý, ví dụ có thể là các module truyền thông với nhau qua 232, hay tcp/ip. Trong trường hợp khi một đối tượng nhất định cần được thông báo thường xuyên về những thay đổi trong các đối tượng khác. Thay vì thường xuyên hỏi vòng (kiểu như modbus RTU) chúng ta có thể cập nhật giá trị có có sự thay đổi trạng thái. ta có thể đăng ký (subcribe) để nhận thông báo (notify) về sự thay đổi hoặc hủy đăng ký nó. Mẫu thiết kế Observer (quan sát) có thể hỗ trợ chúng ta tái sử dụng trong nhiều trường hợp khác nhau. 

### Observer Pattern là gì ?
- Theo [here](https://gpcoder.com/4747-huong-dan-java-design-pattern-observer/), Observer Pattern là một trong những Pattern thuộc nhóm hành vi (Behavior Pattern). Nó định nghĩa mối phụ thuộc một – nhiều giữa các đối tượng để khi mà một đối tượng có sự thay đổi trạng thái, tất các thành phần phụ thuộc của nó sẽ được thông báo và cập nhật một cách tự động.


- Tham khảo về observer pattern tại [wiki](https://en.wikipedia.org/wiki/Observer_pattern) hoặc [here](https://gpcoder.com/4747-huong-dan-java-design-pattern-observer/)




