---
layout: post
title: Cài đặt bộ gõ tiếng việt iBus trên Ubuntu 14.04
---

Khi mới cài đặt Ubuntu 14.04 hoặc 13.10 việc đầu tiên bạn quan tâm đó chính là làm sao để gõ tiếng việt trên Ubuntu. Nếu như thời gian trước việc cài đặt Unikey gõ tiếng việt khá khó khăn thì với những phiên bản mới gần đây, việc cài đặt đã trở nên đơn giản và dễ dàng. Bên cạnh đó, bộ gõ tiếng việt iBus cũng được trang bị thêm nhiều tính năng mới trên Ubuntu.

Hiện nay, iBus là bộ gõ tiếng việt tốt nhất trên Ubuntu mà bạn nên cài đặt vào máy tính của mình. Unikey iBus khi được cài đặt trên Ubuntu 14.04 đã được tích hợp gần giống với Unikey trên Window. Bạn có thể chuyển đổi qua lại giữa 2 kiểu gõ TELEX và VNI đồng thời bạn cũng có thẻ sử dụng nhiều bảng mã khác nhau (Unicode, VNI Windows,...).

#### Cách cài đặt bằng terminal

1. Thêm PPA của Ubuntu VN

```bash
$ sudo add-apt-repository ppa:ubuntu-vn/ppa
$ sudo apt-get update
```
2. Cài iBus

```bash
$ sudo apt-get install ibus-unikey
$ ibus restart
```

3. Mở Text Entry

Bạn tiến hành mở Text Entry trong phần tìm kiếm Home hoặc vào `System Setting >> Text Entry`

![](/images/ibus-1.png)

4. Bạn tìm chọn vào dấu **+** >> Tìm với từ khóa Unikey >> Chọn Vietnamese (Unikey) >> Add. Khi đó bạn đã thực hiện thành công việt chèn bộ gõ tiếng việt ibus vào Ubuntu.

![](/images/ibus-2.png)

Để chuyển đổi giữa gõ tiếng việt có dấu và không dấu thuận tiện, bạn có thể đặt tổ hợp phím tắt giống như trong Unikey trong Window hoặc tùy chỉnh phím tắt theo ý của bạn.

![](/images/ibus-3.png)

Giao diện Unikey iBus sau khi cài đặt thành công.

![](/images/ibus-4.png)



