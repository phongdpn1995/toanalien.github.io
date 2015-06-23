---
layout: post
title: Cài đặt và sử dụng HJSplit trên Ubuntu
---
HJSplit là một công cụ mạnh mẽ dùng để chia nhỏ và gộp file, tương thích trên tất cả nền tảng như Windows, Linux, MAC,...

![](/images/hjsplit.jpg)

### 1. Cài đặt JRE

```bash
$ sudo apt-get update
$ sudo apt-get install default-jre
$ sudo java -version
```

### 2. Download HJSplit

```bash
$ wget http://www.freebyte.com/download/hjsplit/hjsplit_g.jar
```

### 3. Chuyển vào thư mục opt

```bash
$ sudo mkdir /opt/hjsplit
$ sudo mv hjsplit_g.jar /opt/hjsplit
```

### 4. Khởi động HJSplit 

```bash
$ /opt/hjsplit/ && java -jar hjsplit_g.jar
```

