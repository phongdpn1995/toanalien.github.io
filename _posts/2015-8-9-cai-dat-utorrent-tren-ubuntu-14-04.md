---
layout: post
title: Cài đặt uTorrent trên Ubuntu Server 14.04
---

![](/images/utorrent-server.png)
<!--break-->
### Bước 1: Download
Download phiên bản uTorrent Server mới nhất, trong bài viết này là bản [alpha 3.3 x64](http://download-new.utorrent.com/track/beta/endpoint/utserver/os/linux-x64-ubuntu-13-04) bản cho Ubuntu 13.04 chạy được trên 14.04.

### Bước 2: Giải nén

- Mở terminal và đổi thư mục làm việc

```bash
cd Downloads/
```
- Giải nén uTorrent vào thư mục /opt

```bash
sudo tar xvzf utserver.tar.gz -C /opt/
```

### Bước 3: Phân quyền

- Phân quyền cho tư mục uTorrent-server

```bash
sudo chmod -R 777 /opt/utorrent-server-alpha-v3_3/
```

### Bước 4: Tạo liên kết

```bash
sudo ln -s /opt/utorrent-server-alpha-v3_3/utserver /usr/bin/utserver
```

### Bước 5: Khởi động

```bash
utserver -settingspath /opt/utorrent-server-alpha-v3_3/
```

**note** nếu bị lỗi `libssl.so`, chạy dòng lệnh

```bash
sudo apt-get install libssl0.9.8:i386
```

### Bước 6 Đăng nhập

- Mở bằng browser URL

```bash
localhost:8080/gui
```

hoặc

```bash
IP:8080/gui
```

*với IP là ip của server*

- Username là `admin`, password để trống.
 




