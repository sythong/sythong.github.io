---
layout: post
title: Exceptions
author: Thong Ho
date: '2019-10-20 21:35:23 +0530'
categories: Computer_system_enginering
summary:  Lập trình về exception
thumbnail: siteleaf.jpg
permalink: /:categories/exceptions
---


## Giới thiệu
- Đã bao giờ bạn lập trình c++ với try-catch exception như đoạn code dưới đây : 

```

#include <iostream>
#include <string>

int main() {
    try{
        throw 6;
    }
    catch(int e) {
        std::cout << "Int exception thrown " << std::to_string(e) << std::endl;
    }
} 

```

- Việc xử lý exception cho phép ngôn ngữ c++ hay các ngôn ngữ khác có thể xử lý các trường hợp ngoại lệ và chúng ta nên dùng nó. Khi sử dụng mechanism này cho phép chúng ta thực hiện các report lôi phức tạp khi chúng xuất hiện.

## Thừa kế lớp Expeption chuẩn. The standard exception class hierarchy

- Thư viện chuẩn cung cấp một lớp exception cơ bản có thể sử dụng và overide the what and ~exception virtual function  trong lớp gốc. Điều này cho phép chúng ta có thể tùy chỉnh các bản tin lỗi (kiểu string) và destructor cho phép chúng ta free any memory allocated on the heap với the operator new function. 

    - Ví dụ:

    ```

    #include <iostream>
    #include <exception>

    using namespace std;

    class derivedexception: public exception {
        virtual const char* what() const throw() {
            return "My derived exception";
        }
    } myderivedexception;

    int main () {
        try {
            throw myderivedexception;
        }
        catch (exception& e) {
            cout << e.what() << '\n';
        }
    }

    ```

    - Kết quả :

    ```

    ppAdvanCourse/exception$ ./exception1
    My derived exception

    ```

    - 2 dòng đầu ta include thư viện chuẩn input, output và exception base class.
    - Dòng thứ 3 khai báo sử dụng namespace std.
    - Dòng thứ 4:

    ```

    class derivedexception: public exception {}

    ```
    khai báo một lớp derived của chung ta gọi là derivedexception và ta truy xuất lớp exception cơ bản như là public members. 

    - Dòng thứ 5:

    ```

    virtual const char* what() const throw()

    ```
    định nghĩa overivedden hàm what của lớp cơ bản trả về (const) (char*) (c string ) "My devired exception.  

