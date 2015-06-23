---
layout: post
title: Lấy danh sách tên file trong thư mục bằng cmd trong windows
---
### 1. Đặt vấn đề
- Khi bạn cần thống kê danh sách các tên file trong 1 thư mục với rất nhiều file khác nhau thì việc làm bằng tay là không thể. Vì vậy, bài viết này sẽ hướng dẫn bạn sử dụng cửa sổ dòng lệnh cmd để dễ dàng lấy danh sách tên file.

### 2. Bắt đầu 
- Trước hết bạn mở cửa sổ dòng lệnh run bằng tổ hợp phím Windows + R

- Gõ cmd > enter

- Cài đặt bản mã UTF8 để hiển thị tiếng Việt

```bash
chcp 65001
```

- Trỏ đến thư mục chứ file, trong trường hợp này là F:\Music\AuMy

```text
F:
cd Music\AuMy
```

- Để lấy danh sách gồm cả ngày tháng, dung lượng file, bạn sử dụng command

```bash
dir > file_list.txt
```

với file_list.txt là file chứa danh sách

- Để lấy danh sách chỉ có tên

```bash
dir /a-d /b > file_list.txt
```

Mở file file_list.txt để lấy thông tin.
