---
layout: post
title: Hướng dẫn sử dụng Windows RDP để remote Ubuntu
---

Trong khuôn khổ bài viết này, tôi sẽ hướng dẫn các bạn cài đặt xRDP trên Ubuntu để remote bằng Windows RDP thay vì sử dụng các soft khác như vnc, teamviewer.

#### Yêu Cầu

Bắt buộc port 3389 trên server phải được hỗ trợ và open. 

### Cài đặt

1. Nếu bạn sử dụng phiên bản ubuntu bạn phải cài đặt môi trường desktop như Unity hoặc GNOME, tôi hướng dẫn bạn cài Unity như bên dưới

```bash
$ sudo apt-get install ubuntu-desktop 
```
2. Cài đặt XRDP

```bash
$ sudo apt-get install xrdp
```
3. Khởi động XRDP

```bash
$ sudo /etc/init.d/xrdp start
```

4. Tạo user đăng nhập

```
$ sudo adduser USERNAME
```

**Chú ý**: Nếu server không chấp nhận tên bạn dùng, vui lòng thêm `--force-badname` vào sau câu lệnh

5. User bạn mới tạo đã có thể login nhưng không thể cài đặt app hoặc thực hiện quyền administrator. Bạn phải cấp quyền sudo cho user

```bash
$ sudo adduser USERNAME sudo
```

6. Mở Remote App trên Windows

```text 
Start -> Run -> mstsc
```

![](/images/mstsc.jpg)

7. Mở tùy chọn

![](/images/XRDP1.jpg)

8. Nhập IP và username

![](/images/XRDP2.jpg)

9. Nếu như desktop hiện trắng, thực hiện các bước

```bash
$ su USERNAME
```

Create a file called .xsession:

```bash
$ nano .xsession
```

thêm dòng 

```text
gnome-session –session=Ubuntu-2d
```
CTRL+X để lưu và thoát, thực hiện lại bước 8. 


**Thêm**: để XRDP tự khởi động ta cần làm như sau

```bash
$ update-rc.d xrdp.sh defaults
```
to add

```bash
$update-rc.d xrdp.sh remove
```
to remove

Vậy là xong, ta đã có thể remote ubuntu = windows rdp :)

