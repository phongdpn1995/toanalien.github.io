---
layout: post
title: Hướng dẫn sử dụng Openshift để deploy ứng dụng NodeJS
---
![](/images/openshift.png)

### 1. Giới thiệu OpenShift

OpenShift là một dịch vụ nền tảng điện toán đám mây của hãng Red Hat.

Phần mềm chạy dịch vụ là mã nguồn mở và có sẵn trên GitHub với tên "OpenShift Origin".

Người phát triển phần mềm có thể sử dụng Git để triển khai ứng dụng bằng các ngôn ngữ khác nhau trên nền tảng.

Đặc biệt, OpenShift cũng hỗ trợ các ứng dụng web dạng phần mềm mã nhị phân, miễn là nó có thể chạy trên RHEL Linux. Điều này làm tăng tính tùy biến của hệ thống, hỗ trợ nhiều ngôn ngữ và frameworks.

OpenShift bảo trì dịch vụ bên dưới ứng dụng và thống kê ứng dụng nếu cần thiết.

### 2. RHC Tool (Red Hat Client tool)

- RHC là một công cụ hỗ trợ client của RedHat, được xây dựng bằng Ruby. Openshift tích hợp với GIT và các vesion control khác cho app của bạn.

- Trong bài viết này tôi sẽ hướng dẫn các bạn sử dụng RHC trên Ubuntu, các OS khác bạn vui lòng tham khảo tại [https://developers.openshift.com/en/managing-client-tools.html](https://developers.openshift.com/en/managing-client-tools.html)

- Cài đặt (mình sẽ hướng dẫn tổng quát, không chú thích )

```bash
$ sudo apt-get install ruby-full
$ sudo apt-get install rubygems-integration
$ sudo gem install rhc
```

- Cấu hình rhc

```bash
$ rhc setup
```
- Tạo ứng dụng đầu tiên với NodeJS và Mongo

```bash
$ rhc app create MyApp nodejs-0.10 mongodb-2.4
```

khi tạo app thành công, output dạng

```text
root@vagrant-ubuntu-trusty-64:~# rhc app create MyApp nodejs-0.1 mongodb-2.4
Using nodejs-0.10 (Node.js 0.10) for 'nodejs-0.1'

Application Options
-------------------
Domain:     toanalien
Cartridges: nodejs-0.10, mongodb-2.4
Gear Size:  default
Scaling:    no

Creating application 'MyApp' ... done

  MongoDB 2.4 database added.  Please make note of these credentials:

   Root User:     admin
   Root Password: WR5XE8Wj4gFd
   Database Name: myapp

Connection URL: mongodb://$OPENSHIFT_MONGODB_DB_HOST:$OPENSHIFT_MONGODB_DB_PORT/

Waiting for your DNS name to be available ... done

Cloning into 'myapp'...
The authenticity of host 'myapp-toanalien.rhcloud.com (52.7.254.2)' can't be established.
RSA key fingerprint is cf:ee:77:cb:0e:fd:02:d7:72:7e:ay:80:c0:90:13:a7.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'myapp-toanalien.rhcloud.com,52.7.254.2' (RSA) to the list of known hosts.

Your application 'myapp' is now available.

  URL:        http://myapp-toanalien.rhcloud.com/
  SSH to:     55c8e5f87628e1617600008e@myapp-toanalien.rhcloud.com
  Git remote: ssh://55c8e5f87628e1617600008e@myapp-toanalien.rhcloud.com/~/git/myapp.git/
  Cloned to:  /root/myapp

Run 'rhc show-app MyApp' for more details about your app.
root@vagrant-ubuntu-trusty-64:~#
```

Bây giờ bạn có thể vô thư mục `/root/myapp` để deploy. :)

- Put code lên OpenShift

```bash
$ git add .
$ git commit -m "first deploy"
$ git push
```

Trên đây là hướng dẫn khái quát sử dụng OpenShift để deploy Nodejs, mình sẽ làm những tut chi tiết hơn, các bạn đón xem. 

Mọi thắc mắc, vui lòng comment bên dưới.

:)
