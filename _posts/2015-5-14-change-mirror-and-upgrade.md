---
layout: post
title: Thay đổi Mirror servers và nâng cấp phiên bản Ubuntu
---
Mặc định Ubuntu sử dụng mirror US, việc này làm cho việc sử dụng lệnh apt-get install, update, upgrade kém hiệu quả vì đường truyền.
Để khắc phục hạn chế trên, ta sẽ thay đổi về dùng mirror Việt Nam.

![](/images/ubuntu15.png)

Một số mirror VN hiện có 

```text
http://mirror-fpt-telecom.fpt.net/ubuntu/
http://mirror.nhanhoa.com/Ubuntu/
http://mirrors.digipower.vn/ubuntu/
http://virror.hanoilug.org/ubuntu/
```

## Cập nhật file sources.list


```bash
$ sudo gedit /etc/apt/sources.list
```

Tìm và thay đổi dòng `http://us.archive.ubuntu.com/ubuntu` thành mirror bạn muốn ví dụ như `http://mirror-fpt-telecom.fpt.net/ubuntu/`

## Nâng cấp phiên bản

Edit file `/etc/update-manager/release-upgrades`

```bash
$ sudo gedit /etc/update-manager/release-upgrades
```

Tìm dòng `Prompt=` sửa thành `Prompt=normal`

### Nâng cấp bằng lệnh 

```bash
$ sudo do-release-upgrade
```


