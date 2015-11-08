---
layout: post
title: Enable remote access of MySql on Ubuntu
---

Mặc định MySQL chỉ nghe thông qua localhost, nếu chúng ta muốn bật remote access, chúng ta cần thay đổi file `my.cnf`
<!--break-->
```bash
sudo nano /etc/mysql/my.cnf
```
![](/images/my.cnf1.png)

![](/images/my.cnf2.png)

Sau khi thay đổi, chúng ta khởi động lại mysql service:

```bash
sudo service mysql restart
```

![](/images/mysql-server.png)

Cấp quyền truy cập `root` với mọi host:

```bash
mysql –u root -p"password"
GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```

*password is root's password*

![](/images/heidisql.png)	

bài gốc [https://rbgeek.wordpress.com/2014/09/23/enable-remote-access-of-mysql-on-ubuntu/](https://rbgeek.wordpress.com/2014/09/23/enable-remote-access-of-mysql-on-ubuntu/)