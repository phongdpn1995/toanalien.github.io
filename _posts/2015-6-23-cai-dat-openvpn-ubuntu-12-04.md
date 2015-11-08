---
layout: post
title: Cài đặt và OpenVPN trên Ubuntu 12.04
---
OpenVPN là một phần mềm mạng riêng ảo mã nguồn mở dành cho việc tạo các tunnel per-to-per được mã hóa giữa các máy chủ. Phần mềm này do James Yonan viết và được phổ biến dưới giấy phép GNU GPL.

![](/images/openvpn.png)
<br>
### Cài đặt cơ bản
Trong bài hướng dẫn này, chúng ta sẽ cài đặt OpenVPN trên máy chủ Ubuntu 12.04
<!--break-->
### Cài đặt OpenVPN
- Trước hết bạn phải chắc chắn rằng đang truy cập vps dưới quyền `root`
- Download openvpn package 
+ bản 64 bit 

```bash
$ sudo wget http://swupdate.openvpn.org/as/openvpn-as-2.0.7-Ubuntu12.amd_64.deb
```

+ bản 32 bit 

```bash
$ sudo wget http://swupdate.openvpn.org/as/openvpn-as-2.0.7-Ubuntu12.i386.deb
```

- cài đặt 
+ 64 bit 

```bash
$ dpkg -i openvpn-as-2.0.7-Ubuntu12.amd_64.deb 
```
+ 32 bit 

```bash
$ dpkg -i openvpn-as-2.0.7-Ubuntu12.i386.deb
```

- Thiết lập password truy cập

```bash
$ sudo passwd openvpn
```

- Quản lý và thiết lập OpenVPN

```bash
Admin  UI: https://YourIpAddress:943/admin
Client UI: https://YourIPAddress:943/
```

Thay đổi YourIpAddress bằng ip vps của bạn. Truy cập bằng username là `openvpn` và password bạn đã đặt.

Download OpenVPN Connect cài đặt và sử dụng. 