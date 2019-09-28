---
layout: post
title: Các phương pháp xử lý tín hiệu analog từ ADC của vi điều khiển
author: Thong Ho
date: '2019-09-19 11:55:23 +0530'
categories: embbed_programming
summary: this blog for learing and sharing knowledge
thumbnail: kalman2.png
permalink: /:categories/methods
use_math: true
---

## Mục đich

Nội dung 
    Giới thiệu 
    Tính năng
    Bộ lọc trung bình
    Bộ lọc thông thấp (cao)
    Bộ lọc kalman



1. Bộ lọc trung bình 

- Giá trị đầu ra được lấy trung bình $n$ mẫu (n samples) theo giá trị đầu vào. 
- Công thức : 

    $$ x_{out}  = \frac{\sum{x_i}}{n}$$

- Code : 
```c++
int AnalogProcessing::getAverageValue(float in_value, float &out_value)
{
  inc_avr ++;  // bat dau tinh tu 1
  if (inc_avr <= number_of_samples)
  {
    sum_average += in_value;
    return -1;
  }
  else
  {
    out_value = (float)sum_average / number_of_samples;
    sum_average = 0;
    inc_avr = 0;
    return 1;
  }
}
```
Ở đây hàm đưa tham số đầu vào m sử dụng dạng tham chiếu. nên khi sử dụng ta cần đưa một biến toàn cục mà bạn muốn lấy dữ liệu. Hàm hàm này có thể được viết lại thêm 1 function chỉ có cập nhật giá trị đầu ra riêng là được. 
- Một số hình ảnh đầu ra : 
![](/assets/img/embedded_programming/analog_processing/adc_average_1.png)

 + Đáp ứng của bộ lọc trung bình khi giá trị thay đổi
![](/assets/img/embedded_programming/analog_processing/adc_average_2.png)


- Bộ lọc thông thấp:
    -- lý thuyết

    -- Code: 
```c++
float AnalogProcessing::getLowPassValue(float value)
{
  out_value_lowpass = alpha_lowpass * out_value_lowpass + (1 - alpha_lowpass) * value;
  return out_value_lowpass;
}
```

![](/assets/img/embedded_programming/analog_processing/lowpass_h1.png){:class="img-fluid"}

Đáp ứng của bộ lọc thông thấp
![](/assets/img/embedded_programming/analog_processing/lowpass_h2.png){:class="img-fluid"}


- Bộ lọc kalman:

- Lý thuyết : 

- Prediction Phase:

    $$\hat{r}_{t} = r_{t-1}$$ 

    $$\hat{P}_t = P_t + R_t$$

- Update phase : 

    $$K_t = \frac{\hat{P}_t}{\hat{P}_t + Q} $$

    $$P_t = (1-K_t)\hat{P}_t$$
    
    $$r_{t} = \hat{r}_{t} + K_t(z_t - \hat{r}_{t})$$


- code c++: 
``` c++
float AnalogProcessing::getKalmanFilterValue(float value)
{
    // update phase
  kalman_gain = err_estimate/(err_estimate + err_measure);  // tinh toan sai so uoc luong
  kalman_current_estimate = kalman_last_estimate + kalman_gain*(value - kalman_last_estimate);  // cap nhat gia tri hien tai 
// prediction phase
  err_estimate = (1.0 - kalman_gain) * err_estimate + fabs(kalman_last_estimate - kalman_current_estimate)*err_process;
  kalman_last_estimate = kalman_current_estimate;

  return kalman_current_estimate;
}
```

![](/assets/img/embedded_programming/analog_processing/kalman1.png){:class="img-fluid"}

Đáp ứng của bộ lọc lâmn
![](/assets/img/embedded_programming/analog_processing/kalman2.png){:class="img-fluid"}

![](/assets/img/embedded_programming/analog_processing/kalman3.png){:class="img-fluid"}


