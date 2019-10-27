---
layout: post
title: Smart pointers
author: Thong Ho
date: '2019-10-20 21:35:23 +0530'
categories: Computer_system_enginering
summary:  smart pointers
thumbnail: siteleaf.jpg
permalink: /:categories/smart-pointers
use_math: true
---


## Giải pháp smart pointer :
- Smart pointers là những lớp class (lớp) quản lý con trỏ trong ngôn ngữ C++, nó cung cấp hàm destructor được tự động gọi đến khi đối tượng của class đó đi ra khỏi phạm vi khối lệnh chứa nó. Vậy, nếu chúng ta cấp phát vùng nhớ cho nó trong phần khởi tạo (constructor), vùng nhớ đó sẽ được đảm bảo giải phóng khi đối tượng smart pointer bị hủy.

- Ngôn ngữ C++ cung cấp cho chúng ta 4 loại smart pointer khác nhau: std::auto_ptr, std::unique_ptr, std::shared_ptr, and std::weak_ptr.


## Unique pointer
- std::unique_ptr là một giải pháp thay thế cho std::auto_ptr trong chuẩn C++11. Nó được sử dụng để quản lý các vùng nhớ mà không cấp quyền sử dụng chung tài nguyên cho các đối tượng khác. std::unique_ptr được định nghĩa trong thư viện .

- Examples:
```
    #include <iostream>
    #include <string>
    #include <memory> // for std::unique_ptr

    struct Resource
    {
        Resource() { std::cout << "Resource acquired\n"; }
        ~Resource() { std::cout << "Resource destroyed\n"; }
        
        std::string getData() { return "I'm data"; }
    };

    int main()
    {
        std::unique_ptr<Resource> res(new Resource);

        if(res)
        {
            std::cout<< (*res).getData() << std::endl;
        }

        return 0;
    }
```


## Share pointer

- Example:

```

#include <iostream>
#include <memory> // for std::shared_ptr
 
using namespace std;
struct Resource
{
public:
	Resource() { std::cout << "Resource acquired\n"; }
	~Resource() { std::cout << "Resource destroyed\n"; }
};
 
int main()
{
	// allocate a Resource object and have it owned by std::shared_ptr
	Resource *res = new Resource;
	std::shared_ptr<Resource> ptr1(res);
	{
		std::shared_ptr<Resource> ptr2(ptr1); // use copy initialization to make another std::shared_ptr pointing to the same thing
 
		std::cout << "Killing one shared pointer\n";
	} // ptr2 goes out of scope here, but nothing happens
 
	std::cout << "Killing another shared pointer\n";
 

    std::shared_ptr<Resource> p1(new Resource);
    {
        std::shared_ptr<Resource> p2(p1);
        std::cout << "kill p1"<<endl;
    }
    std::cout<< "kill p2" <<std::endl;
	return 0;
} // ptr1 goes out

```