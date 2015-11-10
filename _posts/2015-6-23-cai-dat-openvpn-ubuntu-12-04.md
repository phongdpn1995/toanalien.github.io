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

Để bắt đầu quá trình cài đặt bạn chạy lệnh sau:

```
wget git.io/vpn --no-check-certificate -O openvpn-install.sh; bash openvpn-install.sh
```

Sau đó script sẽ tự động cài đặt, cuối cùng bạn sẽ có file `clientname.ovpn` trong thư mục `/root` để kết nối tới server.

Để tiếp tục thêm user, bạn chỉ cần sử dụng lệnh bash `openvpn-install.sh`



- Quản lý và thiết lập OpenVPN

```bash
Admin  UI: https://YourIpAddress:943/admin
Client UI: https://YourIPAddress:943/
```

Thay đổi YourIpAddress bằng ip vps của bạn. Truy cập bằng username là `openvpn` và password bạn đã đặt.

Download OpenVPN Connect cài đặt và sử dụng. 