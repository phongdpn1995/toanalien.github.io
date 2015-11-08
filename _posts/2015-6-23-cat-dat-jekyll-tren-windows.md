---
layout: post
title: Cài đặt Jekyll trên Windows
---
[Jekyll](http://github.com/jekyll/jekyll) Transform your plain text into static websites and blogs.

![](/images/jekyll-logo.png)

Trước hết mình xin giới thiệu về Jekyll. Jekyll là một dạng teamplate chạy trên nền Ruby giúp người dùng có thể biến những văn bản viết bằng ngôn ngữ Markdown thành một blog đơn giản mà không cần sử dụng đến hệ cơ sở dữ liệu hoặc bất kì dòng code phức tạp nào cả.

Mình có 1 bài hướng dẫn nhanh để các bạn có thể tạo ngay blog trên github [tại đây](../viet-blog-tren-github/).
<!--break-->
### Chuẩn bị

- Ruby [2.2.2](http://rubyinstaller.org/downloads/)
- Ruby Development Kit [4.7.2](http://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe)
- RubyGems [2.4.8](http://production.cf.rubygems.org/rubygems/rubygems-2.4.8.zip)	
- Python [2.7.10](https://www.python.org/ftp/python/2.7.10/python-2.7.10.msi)

### Bắt đầu cài đặt
#### Cài đặt Ruby với tùy chỉnh như hình 

![](/images/install-ruby-1.PNG)

kiểm tra cài đặt 

```bash
$ ruby -v
ruby 2.2.2p95 (2015-04-13 revision 50295) [x64-mingw32]
```

#### Cài đặt Gems
- Giải nén rubygems-2.4.8.zip, đi đến thư mục
```bash
$ cd rubygems-2.4.8
$ ruby setup.rb
```

kiểm tra cài đặt

```bash
$ gem -v
```

#### Cài đặt DevKit
+ giải nén gói `DevKit-mingw64-64-4.7.2-20130224-1432-sfx`
+ đi đến thư mục `devkit`
+ cài đặt bằng lệnh 

```bash
$ ruby dk.rb init
$ ruby dk.rb review
$ ruby dk.rb install
```

#### Cài đặt Jekyll

```bash
$ gem install jekyll
```

#### Cài đặt Python
- chạy file setup python, sau đó thêm biến môi trường

`System Properties > Environments Variables > System Variables > Path`

thêm dòng  

```text
C:\Python27;C:\Python27\Scripts;
```

kiểm tra cài đặt 

```bash
$ python --version
Python 2.7.10
```

#### Cài đặt Pygments thông qua Easy_install

- download [ez_setup.py](../resources/ez_setup.py)

- cài đặt easy_install

```bash
$ python "C:\ez_setup.py"
```

- kiểm tra cài đặt

```bash
$ easy_install --version
setuptools 17.1.1
```

- cài đặt Pygments

```bash
easy_install Pygments
```

#### Tạo blog mới với Jekyll

```bash
jekyll new myblog
cd myblog
jekyll serve
```

*myblog* là folder chứ jekyll bạn mong muốn.


### Bắt và sửa lỗi 

1 Thông báo lỗi

```bash
"python" is not recognized as an internal or external command, operable program or batch file.
```
"python" hoặc có thể là ruby, gem, easy_install

- Nguyên nhân: chưa thêm biến môi trường 
- Khắc phục: thêm dòng `;C:\Python27` trong biến path environments

2 Thông báo lỗi

```bash
ERROR:  Error installing jekyll:
ERROR: Failed to build gem native extension.

"C:/Program Files/Ruby/Ruby200-x64/bin/ruby.exe" extconf.rb

creating Makefile
make generating stemmer-x64-mingw32.def
compiling porter.c
...
make install
/usr/bin/install -c -m 0755 stemmer.so C:/Program Files/Ruby/Ruby200-x64/lib/ruby/gems/2.0.0/gems/fast-stemmer-1.0.2/li
/usr/bin/install: target `Files/Ruby/Ruby200-x64/lib/ruby/gems/2.0.0/gems/fast-stemmer-1.0.2/lib' is not a directory
make: *** [install-so] Error 1
```

- Nguyên nhân: đường dẫn cài ruby có khoảng trắng (space)
- Khắc phục: Cài lại ruby ở ngoài thư mục Program Files hoặc bất kì thư mục nào không có khoảng trắng

3 Thông báo lỗi

```bash
Generating... Liquid Exception: No such file or directory - python c:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/pygments.rb-0.4.2/lib/pygments/mentos.py in 2013-04-22-yizeng-hello-world.md
```

- Nguyên nhân: cấu hình PATH cho Pygments chua đúng
- Khắc phục: kiểm tra đường dẫn trong PATH

4 Thông báo lỗi

```bash
Generating... Liquid Exception: No such file or directory - /bin/sh in _posts/2013-04-22-yizeng-hello-world.md
```

- Nguyên nhân: Không tương thích với phiên bản Pygments.rb 0.5.1/0.5.2.
- Khắc phục: downgrade phiên bản

```bash
gem uninstall pygments.rb --version 0.5.2
gem install pygments.rb --version 0.5.0
```

5 Thông báo lỗi 

```bash
Generating... You are missing a library required for Markdown. Please run:
$ [sudo] gem install rdiscount
Conversion error: There was an error converting '_posts/2013-04-22-yizeng-hello-world.md/#excerpt'.

ERROR: YOUR SITE COULD NOT BE BUILT:
   ------------------------------------
   Missing dependency: rdiscount
```

- Nguyên nhân: không tìm thấy package `rdiscount`
- Khắc phục: cài đặt rdiscount 

```bash
gem install rdiscount
```

6 Thông báo lỗi

```bash
c:/Ruby200-x64/lib/ruby/site_ruby/2.0.0/rubygems/core_ext/kernel_require.rb:55:in `require': cannot load such file -- wdm (LoadError)
from c:/Ruby200-x64/lib/ruby/site_ruby/2.0.0/rubygems/core_ext/kernel_require.rb:55:in `require'
from c:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/listen-1.3.1/lib/listen/adapter.rb:207:in `load_dependent_adapter'
from c:/Ruby200-x64/lib/ruby/gems/2.0.0/gems/listen-1.3.1/lib/listen/adapters/windows.rb:33:in `load_dependent_a
dapter'
...
```

- Nguyên nhân: không tìm thấy package `wdm`
- Khắc phục: cài đặt wdm

```bash
gem install wdm
```

### Thành quả cuối cùng 

![](/images/jekyll-site.PNG)