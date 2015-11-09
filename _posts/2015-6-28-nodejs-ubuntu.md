---
layout: post
title: Hướng dẫn cài đặt NodeJS trên Ubuntu 14.04
---
![](/images/nodejs-ubuntu.png)

<!--break-->

Có rất nhiều cách để cài NodeJS:

 + 1: thông qua packages mặc định của Debian/Ubuntu “node” và “npm”.
 + 2: thông qua Debian/Ubuntu packages tạo bởi Node.js team.
 + 3: thông qua binary packages từ website NodeJS.
 + 4: thông qua Github source repository.

### Cài đặt

Trong bài hướng dẫn này, chúng ta sẽ tìm hiểu cách cài đặt  thứ nhất, đơn giản và tiện lợi nhất

```bash
$ sudo apt-get remove --purge node // gở bỏ phiên bản cũ
$ curl --silent --location https://deb.nodesource.com/setup_0.12 | sudo bash -
$ sudo apt-get install --yes nodejs
$ sudo ln -s /usr/bin/nodejs /usr/bin/node // tạo symbolic link
```

kiểm tra 

```bash
$ node -v
v0.10.25
$ npm -v
1.3.10
```

