---
layout: post
title: Hướng dẫn cài đặt Raspbian OS
---

- Trong bài này mình sẽ hướng dẫn các bạn cách cài đặt Raspbian OS lên trên thẻ SD để chạy trên Paspberry Pi mainboard. 

- Đầu tiên chúng ta cần có :
	- Raspberry Pi mainboard
	- Nguồn
	- Thẻ SD + đầu đọc hoặc adapter
	- Cáp usb mini
	- Cáp Lan
	- Raspbian image download tại [Download Page](https://www.raspberrypi.org/downloads/raspbian/) hoặc [Direct Link](http://director.downloads.raspberrypi.org/raspbian/images/raspbian-2015-05-07/2015-05-05-raspbian-wheezy.zip)
	- Phần mềm bung img: mình dùng windows nên dùng [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/files/Archive/)
	- [Bitvise SSH Client](http://dl.bitvise.com/BvSshClient-Inst.exe)

### Tiến hành cài đặt

1. Bung image ra usb 
- Chọn phân vùng (thẻ sd), chọn file image, và **Write**

![](/images/win32diskimager.png)

2. Khởi động trên Raspberry Pi
- lắp thẻ nhớ vào mainboard
- cắm cáp LAN nối từ mainboard qua laptop
- cắm nguồn
- **chờ khởi động tầm 1p** sau đó dùng Bitvise SSH Client để kết nối 

```text
IP: 169.254.211.103
PORT: 22
Username: pi
Initial method: Password
Password: raspberry
```

Sau khi login thành công gõ `uname -a` để xem phiên bản linux.


![](/images/raspbian-ssh.png)

- Đến bước này là bạn đã cài đặt thành công Raspbian trên PI mainboard. Giờ bạn đã có thể SSH vào và control như một máy tính thực sự. Bài tiếp theo mình sẽ hướng dẫn cài đặt VNC Server để remote desktop.

- Nếu có thắc mắc, các bạn vui lòng comment bên dưới.

Chúc vui ! :)
