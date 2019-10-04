---
layout: post
title: Lập trình c++ cơ bản (pointers, Arrays, stuctures)
author: Thong Ho
date: '2019-2-2 21:35:23 +0530'
categories: Computer_system_enginering
summary:  Khoa hoc cho arduino
thumbnail: siteleaf.jpg
permalink: /:categories/pointers
---

# BASIC C++ PROGRAMMING

## Pointers
-  Mỗi biến được lưu trữ trong bộ nhớ máy tính tại một nơi nào đó với địa chỉ nhất định. 
- Một con trỏ giữ giá trị ví dụ như một địa chỉ.
ví dụ :
``` cpp
    char ch = ‘Q’;
    char* p = &ch;
    cout << *p;
    ch = ‘Z’;
    cout << *p;
```

- Con trỏ được sử dụng rất nhiều trong các ứng dụng lập trình C và C++. Và nó cũng là một trong những chủ đề khó có thể thiết trong các bài test phỏng vấn. 

##  Arrays 
- Là tập hợp các thành phần có cùng loại với nhau
- Example :
```cpp
    double f[3]
    double* p[10]
    f[2] = 25.3;
    p[4] = &f[2];
    cout << *p[4];
```

## Structures 
- is useful for storing an aggretion of elements.
- Struct thường để tập hợp các thành phần thuộc tính có cùng chung một mối liên hệ nào đó. Ta sẽ gom các nhóm đó lại vs nhau. Đối với c++ thì struct cũng thường được coi như là một class. 
```cpp
enum MealType {NO_PREF, REGULAR, LOW_FAT, VEGETARIAN};
struct Passenger {
string name;
MealType mealPref;
bool isFreFlyer;
string freFlyerNo;
};
```

## Example of pointers and Arrays
```cpp
char c[] = {‘c’, ‘a’, ‘t’};
char *p=c;
char *q=&c[0];
cout << c[2] << p[2] << q[2];
```

## Allocate a new instance  (cấp phát bộ nhớ)
- Sử dụng toán tử new
```cpp
p = new Passenger;
//…
p‐>name = “Pocahontas”;
p‐>mealPref = REGULAR;
p‐>isFreqFlyer = false;
p‐>freqFlyerNo = “NONE”;
//…
delete p;
```
- Lưu ý: Khi cấp phát một đối tượng bằng toán tử 'new' , thì cuối cùng khi kết thúc nên sử dụng toán tử "delete" để giải phóng vùng nhớ đã được cấp phát.

##  Namespaces
- is a machanism that allows a group of related names to be define in one place.
- Ex: 
```cpp
namespace myglobal {
int cat;
string dog = “bow bow”;
}
//…
myglobal::cat = 1;
```
- The using statement:
```cpp
using std::string //makes std::string accessible
using std::cout //make std::cout accessible
using namespace myglobals //makes all of myglobals accessible
```

## scope (phạm vi của biến)
- Local, global and static variable:
    - Local : sử dụng trong phạm vi fucntion được khai báo. sau khi thoát ra khỏi thì địa chỉ lưu trữ biến được giải phóng.
    - Global: Giá trị lưu trữ toàn cục trong suốt quá trình hoạt động.
    - static : phạm vi truy cập thì như local, và giá trị được giữ lại như global




# MỘT SỐ BÀI TẬP THI LIÊN QUAN

1. Bài 1 :  Given A following C++ declaration  (đề thi giữa kì học kỳ 1 năm 2018-2019)
    ```cpp
        string A[] = {"computer", "calculator","process","system","engineering","technology"};
        string *p; 
    ```
    - a. Use the pointer p to print the element “process” of the array A, and show it on the screen.
    
        - Solution:
        ```cpp
            string t = *(p+2);
            cout << t << endl;	
        ```
    - b. Declare a pointer q, and copy the address of the element A[2] to the pointer q, and show this address on the screen.
        - Solutiono: 
        ```cpp
            string *q = &A[2];
            cout << q << endl;
        ```
    - c. Combine words from the array A and show the phrase “computer system engineering” on the screen.
        - Solution:
        ```cpp
            string z = A[0] + " "+ A[3] + " " + A[4];
            cout << z << endl; 
        ```
    - d. Use the pointer p to exchange the values of A[0] and A[2].
        - Solution:
        ```cpp
            string d = *p;
            *p = *(p+2);
            *(p+2) = d;
        ```


2.  Bài 2: (Midterm semester 2, 2018-2019 ) Given A following C++ declaration:

```cpp
string A[] = {"Bach", "Khoa","office","international","study","program"};
string *p = A;
```
- a. Use the pointer p to print the element “office” of the array A, and show it on the screen.
    - Solution:
    ```cpp
    string t = *(p+2);
    cout << t << endl;	
    ```
- b. Declare a pointer q, and copy the address of the element A[4] to the pointer q, and show this address on the screen.
    - Solution:
    ```cpp
    string *q = &A[4];
    cout << q << endl;
    ```
- c. Combine words from the array A and show the phrase “international study program” on the screen. 
    - Solution: 
    ```cpp
    string z = A[3] + " "+ A[4] + " " + A[5];
    cout << z << endl; 
    ```
- d.  Use the pointer p to exchange the values of A[0] and A[5].
    - Solution:
    ```cpp
    string d = *p;
    *p = *(p+5);
    *(p+5) = d;
    ```


3. Học kỳ 3 (2017-2018):  Give A following C++ declaration:
```cpp
char T[] = {‘b’, ‘k’, ‘o’ , ‘i’, ‘s’, ‘p’};
int *p = T;
```
What shows on the output screen after the following C++ codes. If an instruction makes error, mark with a tick to the corresponding error box. Give short explanation for each C++ instruction.

```cpp
cout << *p;
 // b : the first element of arr

cout << *&*(p+3);	
// i: *&*(p+3) is the value of T[3]

cout <<*&**p;
//x	error, it should be *&*p

cout << **&*&(p+5);	
// p **&*&(p+5) is value of T[5]		
```