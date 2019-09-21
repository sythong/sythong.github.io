---
layout: post
title: Các phương pháp xử lý tín hiệu analog từ ADC của vi điều khiển
author: Thong Ho
date: '2019-09-19 11:55:23 +0530'
categories: embbed_programming
summary: this blog for learing and sharing knowledge
thumbnail: siteleaf.jpg
permalink: /:categories
---

# Một số phương pháp xử lý tín hiệu đọc từ ADC.
## Mục đich

Nội dung 
    Giới thiệu 
    Tính năng
    Bộ lọc trung bình
    Bộ lọc thông thấp (cao)
    Bộ lọc kalman




- **Kết quả**:

 + Bộ lọc trung bình 
![](/assets/img/embedded_programming/analog_processing/adc_average_1.png)

 + Đáp ứng của bộ lọc trung bình khi giá trị thay đổi
![](/assets/img/embedded_programming/analog_processing/adc_average_2.png)


- Bộ lọc thông thấp:
    -- lý thuyết

    -- Code: 

![](/assets/img/embedded_programming/analog_processing/lowpass_h1.png){:class="img-fluid"}

Đáp ứng của bộ lọc thông thấp
![](/assets/img/embedded_programming/analog_processing/lowpass_h2.png){:class="img-fluid"}


- Bộ lọc kalman:

- Lý thuyết : 


$$\hat{r}^{BLE}_{t} = r^{BLE}_{t-1}$$

$$\begin{itemize}
    \item Prediction Phase:
    \begin{equation}
        \begin{split}
            \hat{r}^{BLE}_{t} = r^{BLE}_{t-1},\\
            &\hat{P}_t = P_t + R_t
        \end{split}
    \end{equation}
      
    \item Update Phase:
     \begin{equation}
        \begin{split}
            & K_t = \frac{\hat{P}_t}{\hat{P}_t + Q}\\
            & P_t = (1-K_t)\hat{P}_t \\
            & r^{BLE}_{t} = \hat{r}^{BLE}_{t} + K_t(z_t^{BLE} - \hat{r}^{BLE}_{t})
        \end{split}
    \end{equation}
\end{itemize}$$


<img src="https://latex.codecogs.com/svg.latex?\Large&space;\hat{r}^{BLE}_{t} = r^{BLE}_{t-1}" title="\hat{r}^{BLE}_{t} = r^{BLE}_{t-1}" />


![](/assets/img/embedded_programming/analog_processing/kalman1.png){:class="img-fluid"}

Đáp ứng của bộ lọc lâmn
![](/assets/img/embedded_programming/analog_processing/kalman2.png){:class="img-fluid"}

![](/assets/img/embedded_programming/analog_processing/kalman3.png){:class="img-fluid"}


