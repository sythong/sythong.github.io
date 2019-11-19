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

- Mục tiêu của ta là khi giao tiếp giữa các subject (Đối tượng) thì chuyển từ Poll (hỏi vòng) sang Push (có cập nhật sẽ thông báo).

### Observer Pattern là gì ?
- Theo [here](https://gpcoder.com/4747-huong-dan-java-design-pattern-observer/), Observer Pattern là một trong những Pattern thuộc nhóm hành vi (Behavior Pattern). Nó định nghĩa mối phụ thuộc một – nhiều giữa các đối tượng để khi mà một đối tượng có sự thay đổi trạng thái, tất các thành phần phụ thuộc của nó sẽ được thông báo và cập nhật một cách tự động.

- Tham khảo về observer pattern tại [wiki](https://en.wikipedia.org/wiki/Observer_pattern) hoặc [here](https://gpcoder.com/4747-huong-dan-java-design-pattern-observer/)
- Tham khảo chính [thisbog](http://osdevlab.blogspot.com/2016/05/observer-design-pattern-in-arduino.html)

- Trong bài này, chúng ta sẽ khám phá thiết kế mẫu observer trên board Arduino. Thường thiết kế mẫu được sử dụng trong các ngôn ngữ lập trình hướng đối tượng (java, c++, c#,...). Ta có sử dụng callback function sẽ dễ dàng hơn, tuy nhiên vấn đề là callback function là static và ta không thể sử dụng std::function (standard c++ library) trên board Arduino.

## Class Design ( Mô hình hóa)
- Mối quan hệ ở đây là 1 to many. Observables (subjects) have many Observers. 
- Mô hình UML như ở hình vẽ:
![classdesign](/assets/img/embedded_programming/observer-arduino/Observer.svg)

- Ta có 3 classes: 
  - Observer
  - ObserverTester (Concrete class)
  - Subject

- Chú ý rằng, mô hình này không publish-subcribe pattern mà sử dụng một phương pháp khác để update trạng thái. The pattern design gồm : *Observer* sẽ attach the *subject* to itself. Khi subject (Đối tượng ) muốn thông báo một số trạng thái cập nhật, nó sẽ notify cho Observer. Khi observer nhận được notified, observer sẽ thực hiện actions trên giá trị nhận được. *ObserverTester* được bắt nguồn từ observer, do đó các observer khác nhau có thể được maintain như observer pattern.

## Thực hiện
1. Observer class :
- Class này chỉ có một  một function cơ bản và một virtual function
- Observer.h

  ```cpp
  class Subject;

  class Observer {
  public:
      void attachSubject(Subject *subject);
      virtual void onReceivedDataFromSubject(const Subject*) = 0;
  };
  ```

- Observer.cpp

  ```cpp
  #include "Observer.h"
  #include "Subject.h"

  void Observer::attachSubject(Subject * subject) {
      subject->registerObserver(this);
  }
  ```

2. Subject (Observable)

- The subject class có thể register và unregister một obsever và nó có thể hold một observer. It sẽ notify một observer nếu có sự thay đổi giá trị. 
- Subject.h

  ```cpp
  class Observer;

  class Subject {
  public:
      Subject();
      void registerObserver(Observer*); 
      void unregisterObserver();
      int getValue() const;
      void setVal(const int val);

  private:
      int mValue;
      void _notifyObserver();
      Observer* mObserver;
  };
  ```

- Subject.cpp

  ```cpp
  #include "Subject.h"
  #include "Observer.h"

  Subject::Subject() {
  }

  void Subject::registerObserver(Observer* obs) {
      mObserver = obs; //we will only allow one observer
  }

  void Subject::unregisterObserver() {
      mObserver = nullptr;
  }

  int Subject::getValue() const {
      return mValue;
  }

  void Subject::_notifyObserver() {
      if (mObserver != nullptr) {
          mObserver->onReceivedDataFromSubject(this); 
      }
  }

  void Subject::setVal(const int val) {
      mValue = val;
      _notifyObserver(); //since there is a change in value, notify the observer
  }
  ```