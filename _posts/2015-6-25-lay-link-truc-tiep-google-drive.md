---
layout: post
title: Lấy link trực tiếp (direct link) Google Drive
---

![](/images/google_drive.png)

<!--break-->

- Việc lấy link trực tiếp sẽ giúp bạn thuận lợi hơn trong việc chia sẻ và download file.

### 1. Lợi ích
- Các downloader có thể add trực tiếp link vào trình download như IDM hoặc EagleGet mà không cần thông qua browser.
- Resume khi lỗi
...

### 2. Chi tiết
- Vào [https://drive.google.com/](https://drive.google.com/) tạo 1 folder chứa file cần lấy link
- Set folder ở chế độ share công khai

![](/images/drive-1.png)

B.1

![](/images/drive-2.png)

B.2

![](/images/drive-3.png)

B.3

- Sau đó ta được link thư mục dạng như 

```text
https://drive.google.com/folderview?id=0BzvzKqSXOTtafkNvYVFGWmJ1a25yRmR3blB0eUVVYnk3TDdpX0wycW4yczE0UXowdmE2MkU&usp=sharing
```

ta sẽ lấy id dạng như 

```text
0BzvzKqSXOTtafkNvYVFGWmJ1a25yRmR3blB0eUVVYnk3TDdpX0wycW4yczE0UXowdmE2MkU
```

- Tiếp theo ta hoàn chỉnh URL dạng 

```text
http://googledrive.com/host/id_folder/ten_file
```

- Trong ví dụ ta có tên file là `Autocad2015x64.iso`, vậy ta có link như sau 

![](/images/drive-4.png)

```text
http://googledrive.com/host/0BzvzKqSXOTtafkNvYVFGWmJ1a25yRmR3blB0eUVVYnk3TDdpX0wycW4yczE0UXowdmE2MkU/Autocad2015x64.iso
```

- Vậy ta đã có được 1 direct link hoàn chỉnh.

**- Mẹo**: 
 + Các file sau này lưu trong cùng thư mục chia sẻ sẽ cũng được lấy link như dạng trên, chỉ cần thêm tên file sau đoạn

 ```text
 http://googledrive.com/host/0BzvzKqSXOTtafkNvYVFGWmJ1a25yRmR3blB0eUVVYnk3TDdpX0wycW4yczE0UXowdmE2MkU/
 ```
