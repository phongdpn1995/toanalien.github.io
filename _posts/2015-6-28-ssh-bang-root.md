---
layout: post
title: Login VM Vagrant bằng tài khoản Root
---
### 1. Đặt vấn đề
- Mặc định máy ảo Vagrant không có phép ssh remote trực tiếp bằng account root mà chỉ có thể sử dụng account guest là `vagrant` và password là `vagrant`

### 2. Hướng dẫn
- Để có thể ssh bằng account root, trước hết ta ssh bằng account vagrant sau đó thay đổi 1 số thông số.

```bash
$ vagrant ssh
$ su -
// chờ nhập pass account root là vagrant
$ sudo nano /etc/ssh/sshd_config
```

- tìm dòng 

```text
PermitRootLogin without-password
```
đổi thành 

```text
PermitRootLogin yes
```

lưu và thoát
- khởi động lại ssh

```bash
$ service ssh restart
```

- Mở putty login bằng info

```text
Host Name: localhost
Port: 2222
User: root
Pass: vagrant
```

:)


