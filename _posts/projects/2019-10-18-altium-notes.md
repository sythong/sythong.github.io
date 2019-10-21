---
layout: post
title: Các ghi chú sử dụng altium designer
author: Thong Ho
date: '2019-10-18 07:35:23 +0530'
categories: projects
summary:  Hướng dẫn sử dụng altium
thumbnail: siteleaf.jpg
permalink: /:categories/altium
---


## Phím tắt bên thiết kế mạch nguyên lý (Schematic)

```
Phím tắt	Chức năng
X	Quay linh kiện theo trục X (Đối xứng qua trục X).
Y	Quay linh kiện theo trục Y (Đối xứng qua trục Y).
Space	Xoay linh kiện 90 độ.
, SPACE	Đổi màu khi dùng bút Highlight (Đánh dấu các NET cùng tên)
ALT + Click (chọn Net)	Highlight những Net có cùng tên (Làm mờ toàn bộ các phần còn lại của bản vẽ SCH)
Shift + Ctrl + C	Clear mọi áp dụng trên SCH
Ctrl + Click và kéo	Di chuyển linh kiện đi cùng với dây (Giống như trong Proteus)
Shift + Space	Xoay linh kiện 45 độ.
Shift + Left Click	Copy linh kiện.
Shift + Click và kéo	Kéo linh kiện ra.
Ctrl+Shift+L (hoặc A L)	Căn chỉnh các linh kiện thẳng hàng dọc.
Ctrl+Shift+T (hoặc A T)	Căn chỉnh các linh kiện thẳng hàng ngang.
Ctrl+Shift+H (hoặc A H)	Căn chỉnh các linh kiện cách đều nhau theo hàng ngang.
Ctrl+Shift+V (hoặc A V)	Căn chỉnh các linh kiện cách đều nhau theo hàng dọc.
Ctrl + M	Đo khoảng cách.
C C	Biên dịch Project - Kiểm tra các lỗi kết nối, port.
D B	Lấy linh kiện trong thư viện.
D O	Thay đổi thông số bản vẽ.
D U	Update nguyên lý sang mạch in.
J C	Nhảy đến linh kiện.
P B	Vẽ đường bus.
P N	Đặt tên cho đường dây.
P O	Lấy GND.
P T	Thêm Text.
P W	Để đi dây nối chân linh kiện.
P V N	Đánh dấu chân không dùng.
T A	Mở cửa sổ quản lý đặt tên cho linh kiện.
T N	Đặt tên tự động cho linh kiện.
T S	Tìm linh kiện bên mạch in (Bạn chọn khối bạn cần đi dây bên mạch nguyên lý rồi ấn T-S, nó sẽ tự động tìm khối đấy bên mạch in cho bạn).
T W	Tạo linh kiện mới
TAB	Thay đổi các thông số của mạch.
V D	Đưa bản vẽ vừa trong khung màn hình.

```

## Các phím tắt khi layout bên altium
```
Phím tắt	Chức năng
2	Xem mạch in ở dạng 2D.
3	Xem mạch in ở dạng 3D.
Q	Chuyển đổi đơn vị mil --> mm và ngược lại.
P T	(Place > Interactive Routing) Chế độ đi dây bằng tay.
P L	Định dạng lại kích thước mạch in nhấn rồi vào lớp keep out layer vẽ đường viền sau đó bôi đen toàn mạch rồi nhấn D S D.
P M (Altium 16) U M (Altium 17)	Kéo nhiều dây 1 lúc (MultiRoute) (bằng cách: nhấn Shift để chọn nhiều Pad, sau đó nhấn [P M] / [U M] rồi đi dây như bình thường. Trong khi MultiRoute, bạn có thể nhấn Tab để điều chỉnh khoảng cách tương đối giữa các dây với nhau)
P G	Phủ đồng.
P V	Lấy lỗ Via.
P R	Vẽ đường mạch to, khoảng cách giữa các đường mạch nhỏ.
P D D	Hiển thị thông tin kích thước PCB (giống như trong Cad có dạng <-- 80mm -->)
A A	Đi dây tự động.
T U A	Xóa bỏ tất cả các đường mạch đã chạy.
T U N	Xóa các đường dây cùng tên.
T D R	Kiểm tra xem đã nối hết dây chưa sau khi hoàn thành đi dây bằng tay.
T E	Bo tròn đường dây gần chân linh kiện (Tea Drop - hình giọt nước cho đường mạch gần chân linh kiện).
T M	Xóa lỗi hiển thị trên màn hình.
D K	Chọn lớp vẽ. (Stack Manager)
D R	Để chỉnh các thông số trong mạch như độ rộng của đường dây (Width), khoảng cách 2 - dây (Clearance),cho phép ngắn mạch (Shortcircuit)...
D O	Chỉnh thông số mạch, nếu bạn không muốn các ô vuông làm ảnh hưởng đến viện vẽ mạch thì chuyển line thành dots.
D T A	Hiển thị tất cả các lớp.
D T S	Chỉ hiển thị lớp TOP + BOTTOM + MULTI...
C K	Mở cửa sổ chỉnh sửa đường dẫn linh kiện.
R B	Hiển thị thông tin mạch (kích thước, số lượng linh kiện...)
O D (Hoặc Ctrl + D)	Hiện thị cửa sổ Configurations (Điều chỉnh ẩn hiện các thành phần)
V B	Xoay bản vẽ 180 độ.
V F	Hiển thị toàn bộ bản vẽ.
L	Khi đang di chuyển linh kiện lật linh kiện giữa lớp Top và Bottom (Bottom và Top)
L hoặc Ctrl+L	Mở View Configuration để điều chỉnh hiển thị các lớp.
TAB	Hiện cửa sổ thay đổi thông tin khi đang thao tác.
Fliped Board	Lật ngược mạch in.
Ctrl G hoặc G	Cài đặt chế độ lưới.
Ctrl M	Thước đo kích thước mạch.
Shift M	Kính lúp hình vuông.
Shift R	Thay đổi các chế độ đi dây (Cắt - Không cho cắt - Đẩy dây).
Shift S	Chỉ cho phép hiện 1 lớp đang chọn (các lớp còn lại được ẩn).
Shift+Space	Thay đổi các chế độ đường dây (Tự do - Theo luật - Vuông 90 độ - Cong)
Ctrl+Shift+L (hoặc A L)	Căn chỉnh các linh kiện thẳng hàng dọc.
Ctrl+Shift+T (hoặc A T)	Căn chỉnh các linh kiện thẳng hàng ngang.
Ctrl+Shift+H (hoặc A H)	Căn chỉnh các linh kiện cách đều nhau theo hàng ngang.
Ctrl+Shift+V (hoặc A V)	Căn chỉnh các linh kiện cách đều nhau theo hàng dọc.
Ctrl+Shift+Cuộn chuột	Chuyển qua lại giữa các lớp.

```

## Phím tắt trong 3D
```

Phím tắt	Chức năng
0	Xoay board mạch về hướng nhìn gốc
9	Xoay board 90 độ
2	Chuyển sang chế độ 2D khi trong chế độ 3D View
3	Chuyển sang View 3D khi trong chế độ 2D
SHIFT	Đồng thời nhần Shift và Click chuột phải, di chuyển chuột để xoay boad mạch theo các trục X Y Z
V F	Điều chỉnh board mạch vừa khít màn hình
V B	Lật boad mạch
Cuộn chuột	Kéo lên - Kéo xuống
SHIFT + Cuộn chuột	Sang trái - Sang phải
CTRL + Cuộn chuột	Phóng to - Thu nhỏ
CTRL + Di chuyển chuột	Phóng to - Thu nhỏ
CTRL + C	Chụp ảnh góc nhìn hiện tại của board mạch 3D vào Clipboard, để lưu thành file ảnh bạn cần sử dụng tool như Paint chẳng hạn.
T P	Mở cửa sổ Preferences
L	Mở cửa sổ Configurations - Điều chỉnh các thuộc tính hiển thị

```