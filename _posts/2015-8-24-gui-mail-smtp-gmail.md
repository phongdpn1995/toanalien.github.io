---
layout: post
title: Gửi mail smtp gmail
---
![](/images/gmail.png)

<!--break-->

- Việc gửi mail bằng hàm phpsendmail sẽ trở nên khó khăn khi hosting không hỗ trợ, vì vậy sử dụng smtp gmail hoặc các smtp khác để gửi mail sẽ là giải pháp trong trường hợp này. 

- Mở đăng nhập ứng dụng không an toàn trên gmail (allow less secure apps)
	+ truy cập [https://myaccount.google.com/security](https://myaccount.google.com/security) 
	+ tìm đến cuối trang có dòng  **allow less secure apps**  bật **on**

![](/images/secure-smtp.png)

- tắt 2-Step Verification

![](/images/2stepverify.png)

- cấu hình smtp

```text
SMTP server : smtp.gmail.com
SMTP username: tên email đầy đủ có cả sau @
SMTP password: mật khẩu email
SMTP port: 465
SMTP TLS/SSL required: yes
```




