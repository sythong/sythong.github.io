---
layout: post
title: Một số lệnh hữu dụng trong linux
author: Thong Ho
date: '2019-10-25 21:35:23 +0530'
categories: operating-system
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/linux-command
---


## Lệnh xoay màn hình

    ```bash
    xrandr -o left
    # normal
    # invert
    # right
    ```

## Sử dụng Alias trong linux
- Tham khảo tại [here](https://viblo.asia/p/su-dung-alias-trong-linux-qm6RWq4xGeJE)
### Mục đích:
- Tạo ra các dòng lệnh tắt thay thế một lệnh hay một tập lệnh nào đó. Hoặc bạn muốn cá nhân hóa một số lệnh của riêng bạn thì sử dụng *alias* là một lựa chọn
- Ví dụ gỡ *update* thay vì *sudo apt-get update*.
### Thiết lập và quản lý Alias.
1. Thêm các alias tạm thời:
- Để thêm một alias mới dùng lệnh: 

    ```bash
    # Them moi
    alias alias_name='aliased_command --options'

    # xóa alias:
    unalias alias_name
    ```

2. Tạo một alias cố định, lâu dài
- Ta có thể lưu câu lệnh trên trong *~/.bashrc* hoặc *~/.bash_profile*.
- Thêm cấu trúc lệnh như ở trên

    ```bash
    alias alias_name='aliased_command --options'
    ```

- Ngoài ra ta cũng có thể lưu riêng các alias ra 1 file khác ví dụ ~/.alias. Nếu  Trong *.bashrc* file ta có thể thêm đoạn script trong *.bashrc* file

    ```bash
    if [ -e $HOME/.alias ]; then
        [ -n "$PS1" ] && . $HOME/.alias
    fi
    ```

- Sau khi xong thì tắt terminal bật lại hoặc nhập lệnh :

    ```bash
    source ~/.bashrc
    # hoặc
    . ~/.bashrc
    ```

- Để xem list of alias:

    ```bash
    alias
    ```
3. Quản lý một số *alias* thông dụng
- Gói quản lý:

    ```bash
    alias ai='sudo apt-get install'
    alias ar='sudo apt-get remove'
    alias au='sudo apt-get update'
    alias aug='sudo apt-get upgrade'
    ```
- Thư mục và file

    ```bash
    alias ..='cd ..'
    alias ...='cd ../..'
    alias ....='cd ../../..'
    alias du='du -h'
    alias df='df -h'
    alias l.='ls -d .* --color=auto'
    alias ls='ls -F --color=auto'
    alias cl='clear && ls'		#Xóa màn hình và hiển thị file, thư mục con
    ```
- OThers

    ```bash
    alias e='exit'
    alias s='sudo'
    alias nnb='nano ~/.bashrc'  #Sửa file alias
    alias rlb='. ~/.bashrc'		#Load lại file alias
    alias h='history'
    ```
4. Alias trong GIT
- Riêng đối với git, ta có thể tạo và xóa các alias tương tự như trên. Tuy nhiên git cũng có cách cài đặt những alias theo cách riêng. Đây là 1 vài ví dụ về thêm mới các alias cho git

    ```bash
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.ci commit
    git config --global alias.st status
    git config --global alias.last 'log -1 HEAD'
    ```
- Để kiểm tra các alias của git ta dùng lệnh

    ```bash
    git config --get-regexp alias
    ```