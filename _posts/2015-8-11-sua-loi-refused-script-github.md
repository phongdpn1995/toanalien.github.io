---
layout: post
title: Sửa lỗi refused file script link từ github
---
![](./images/script-github.png)

Sau khi deploy ứng dụng của mình lên và có sử dụng một số resource có sẵn trên github (vì mình lười pull về rồi push lên :-p) nên đã xảy ra lỗi như hình.



Để khắc phục lỗi trên, ta làm như sau: đổi sang sử dụng **rawgit.com**.

Các bước:

Tìm đến link file trên Github, click xem phiên bản **Raw**.

Copy URL và đổi **raw.github.com** thành **rawgit.com** (non-production) hoặc **cdn.rawgit.com** (production)

Example: 
```text
http://raw.github.com/user/repo/branch/file.js
```

```text
http://rawgit.com/user/repo/branch/file.js
```
```text
http://cdn.rawgit.com/user/repo/tag/file.js
```


#### Vì sao phải cần như vậy ?

Github bắt đầu sử dụng `X-Content-Type-Options: nosniff`, để các trình duyệt hiện đại kiểm tra nghiêm ngặt kiểu MIME. Sau đó nó sẽ trả về file nguyên trong một kiểu MIME được trả về bởi các máy chủ - ngăn chặn các trình duyệt từ việc sử dụng các tập tin như là có dự định (nếu trình duyệt tuân thủ các thiết lập).
