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
two lines close thtwo lines close thtwo lines close th
two lines close th
two lines close th
two lines close th
two lines close th
two lines close th
two lines close th

    ```
    định nghĩa overivedden hàm what của lớp cơ bản trả về (const) (char*) (c string ) "My devired exception. Hai dòng tiếp theo là đóng 




- Ví dụ 4:  sử dụng exception cho 2 vector, update vector2 bị lỗi :
    
```

#include <iostream>
#include <vector>

using namespace std;

void updateVector(std::vector<std::string>& firstvector_, std::vector<std::string>& secondvector_, std::string newString) {
    firstvector_.push_back(newString);
    try {
        secondvector_.push_back(newString);
    }
    catch (...) {
        firstvector_.pop_back();
        cout << "second vector update failed." << endl;
    }
}

void updateVector2(std::vector<std::string>& firstvector_, std::vector<std::string>& secondvector_, std::string newString) {
    firstvector_.push_back(newString);
    try {
        std::bad_alloc excep;
        throw excep;
        secondvector_.push_back(newString);
    }
    catch (...) {
        firstvector_.pop_back();
        cout << "second vector update failed." << endl;
    }
}

int main() {
    std::vector<std::string> firstvector;
    std::vector<std::string> secondvector;
    std::string mystring("Hello world!");

    cout << "Calling updateVector " << endl;
    updateVector(firstvector, secondvector, mystring);

    cout << "first vector size is " << firstvector.size() << " second vector size is " << secondvector.size() << endl;

    cout << "Calling updateVector2 " << endl;

    updateVector2(firstvector, secondvector, mystring);
    cout << "first vector size is " << firstvector.size() << " second vector size is " << secondvector.size() << endl;
}

```

- Kết quả :

```

thongktdt@slam:/media/thongktdt/DATA/2.USN/01_OOP/Cplusplus/cppAdvanCourse/exception$ ./ex4 
Calling updateVector 
first vector size is 1 second vector size is 1
Calling updateVector2 
second vector update failed.
first vector size is 1 second vector size is 1

```

