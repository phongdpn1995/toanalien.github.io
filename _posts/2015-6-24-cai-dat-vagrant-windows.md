---
layout: post
title: Hướng dẫn chi tiết cài đặt, sử dụng Vagrant để tạo máy chủ ảo trên Windows
---
### 1. Đặt vấn đề
- Thông thường khi lập trình web ta hay sử dụng các phần mềm webserver để giả lập môi trường làm việc nhưng môi trường để sản phẩm khi chạy hoàn thiện phần lớn  là Linux, khi đó sẽ có những xung đột về code, moudule và các setup môi trường.
- Khi ta cần thao tác trên máy chủ Linux nhưng ta lại sử dụng Windows hoặc cần giả lập môi trường Linux hoàn toàn mới để thao tác.
- Không muốn mất tiền vào các dịch vụ máy ảo riêng (VPS)

Ở bài này, chúng ta sẽ tìm hiểu một công cụ khác mà bạn có thể sử dụng kèm với VirtualBox hoặc VMWare để tạo máy ảo trong thời gian nhanh nhất, đơn giản nhất và chuyên nghiệp nhất đó là công cụ Vagrant.

### 2. Vagrant là gì ?

- Vagrant là một ứng dụng thêm dành riêng cho VirtualBox và VMWare để hỗ trợ người dùng tạo ra các máy ảo trên máy tính theo nhu cầu của mình và hỗ trợ quản lý toàn bộ máy ảo qua các dòng lệnh, hỗ trợ sẵn các box.
- `box` là một gói hệ điều hành với các thiết lập riêng biệt)
- Với Vagrant bạn có thể chuyển thiết lập các máy ảo trong máy mình sang một máy tính khác (re-package), hoặc cho phép các thành viên cùng team với bạn truy cập vào thư mục riêng trên máy chủ để sửa/xem file mà họ không cần cài đặt bất cứ cái gì, miễn là dùng chung mạng LAN, thậm chí bạn có thể đưa máy chủ của bạn lên môi trường internet chỉ với vài dòng lệnh đơn giản.

### 3. Cài đặt Vagrant
#### 3.1 Cài đặt VirtualBox
Khi sử dụng Vagrant bắt buộc bạn phải cài đặt ứng dụng tạo máy chủ ảo như VirtualBox hoặc VMWare. Bạn nên cài VirtualBox vì nó miễn phí :D

![](/images/virtual-box.png)

#### 3.2 Cài đặt GIT

Chúng ta điều khiển VM qua dòng lệnh linux nên sẽ bất tiện khi dùng `cmd`, do vậy ta cần phần mềm hỗ trợ giả lập môi trường UNIX trên Windows 

- Download GIT tại [http://git-scm.com/download/win](http://git-scm.com/download/win)

![](/images/git-1.png)
![](/images/git-2.png)
![](/images/git-3.png)

Sau khi cài xong, bạn có thể thấy máy tính mình có thêm một ứng dụng tên là Git Bash và Git GUI khi vào menu Start trên máy tính, chúng ta chỉ cần sử dụng Git Bash trong bài viết này.

#### 3.3 Cài đặt Vagrant
- Trước tiên bạn cần truy cập vào [https://www.vagrantup.com/downloads.html](https://www.vagrantup.com/downloads.html) và tải gói cài đặt tương ứng với hệ điều hành mà bạn đang dùng.
- Tải về và cài đặt như một phần mềm bình thường. Cài xong bạn sẽ cần khởi động lại máy tính để hoàn tất. Sau đó là hãy kiểm tra bằng cách mở cái Git Bash lên và gõ `vagrant -h` xem nó có hiện ra các thông tin trợ giúp không. Nếu có thì bạn đã cài Vagrant thành công.

```bash
vagrant -h
Usage: vagrant [options] <command> [<args>]

    -v, --version                    Print the version and exit.
    -h, --help                       Print this help.

Common commands:
     box             manages boxes: installation, removal, etc.
     connect         connect to a remotely shared Vagrant environment
     destroy         stops and deletes all traces of the vagrant machine
     global-status   outputs status Vagrant environments for this user
     halt            stops the vagrant machine
     help            shows the help for a subcommand
     init            initializes a new Vagrant environment by creating a Vagrant
...
```

### 4. Sử dụng Vagrant để tạo máy ảo 

- Trong Vagrant có khái niệm **box**, là một gói hệ điều hành original hoặc đã cài một số ứng dụng cần thiết, chẳng hạn như box CentOS 6.5 64.bit, Ubuntu 12.04 64 bit,... Bạn có thể tải các box về sau đó sử dụng để tạo máy ảo tùy thích.
- Bạn cần có 1 thư mục riêng để chạy máy ảo, thư mục này sẽ chứa các thiết lập cho máy ảo.
- Tất cả thao tác với Vagrant đều qua dòng lệnh.

#### B1. Nạp box cho Vagrant

- Sau khi cài đặt, Vagrant sẽ không có box sẵn mà bạn sẽ phải cần nạp nó về máy. Danh sách các box và đường dẫn của nó bạn có thể xem tại [https://atlas.hashicorp.com/boxes/search](https://atlas.hashicorp.com/boxes/search).

- Bây giờ hãy mở Git Bash lên và tiến hành gõ như sau:

```bash
vagrant box add ubuntu/trusty64
```

**Trong đó**

 + vagrant: đây là cú pháp bắt buộc phải gõ khi muốn dùng ứng dụng vagrant.
 + box: thành phần cần tương tác trên Vagrant, ở đây chúng ta cần tương tác với box.
 + add: hành động cần tương tác với thành phần box.
 + ubuntu/trusty64: tên box cần nạp.

Sau đó chọn VirtualBox.

- **Mẹo**

Bạn có thể download `box` riêng sau đó thêm vào Vagrant bằng cú pháp sau

```bash
vagrant box add boxname file:///d:/path/to/file.box
```

với `boxname` là tên box bạn mong muốn, `file:///d:/path/to/file.box` là đường dẫn đến file box.

- Kiểm tra danh sách box

```bash
vagrant box list
```

#### B2. Tạo máy ảo mới 

- Để tạo máy ảo mới, bạn cần tạo một thư mục riêng cho nó, bạn có thể gõ lệnh dưới để tạo thư mục tên là vm1:

```bash
mkdir vm1
```

Thư mục được tạo ra mặc định sẽ nằm ở `C:\Users\Tên-User\` (Windows) hoặc `/home/$user/` (Linux).

- Đến thư mục 

```bash
cd vm1
```

- Cài đặt máy ảo

```bash
vagrant init trusty64```
với trusty64 là tên box
- thông báo thành công

```bash
D:\vm1>vagrant init trusty64
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

- Bạn có thể cấu hình thêm trong file `Vagrantfile` trong thư mục máy ảo

#### B3. Khởi động máy ảo

```bash
vagrant up
```
![](/images/vagrant-up.png)

#### B4. Truy cập máy ảo qua SSH

```bash
vagrant ssh
```

![](/images/vagrant-vm.png)

#### B4. Cấu hình root 
- Mở file `Vagrantfile` để cấu hình user root

```bash
config.ssh.username = 'root'
config.ssh.password = 'vagrant'
config.ssh.insert_key = 'true'
```

### 5. Bắt và sửa lỗi 

#### 1. Lỗi utf8 Vagrant

![](/images/vagrant-error-1.png)

- Nguyên nhân: đường dẫn đến thư mục `.vagrant.d` có kí tự unicode.
- Khắc phục: 
 + vào `C:\Users\Ten-User` di chuyển thư mục `.vagrant.d` sang ra ngoài (ngoài ổ C hoặc bất kì thư mục nào không có unicode).
 + [thêm biến môi trường](http://www.computerhope.com/issues/ch000549.htm).

```text
VAGRANT_HOME C:\.vagrant.d
```
#### 2. Lỗi utf8 VirtualBox

![](/images/vagrant-error-2.png)

- Nguyên nhân: đường dẫn đến thư mục `Default Machine Folder` có kí tự unicode.
- Khắc phục: thay đổi đường dẫn thư mục `Default Machine Folder`: VirtualBox > File > Preferences > General, đổi đường dẫn.

#### 3. Các lỗi khác
- Kiểm tra đã mở [Virtualization Technology](https://www.google.com/webhp?q=enable+virtualization+technology) trong BIOS chưa ?

### 6. Tổng kết
- Việc cài đặt Vagrant có thể sẽ dễ dàng với các bạn mới bắt đầu, các bạn có thể đọc và làm theo hướng dẫn trên để thiết lập thành công máy ảo trên Vagrant tích hợp VirtualBox.
- Mọi thắc mắc các bạn có thể comment bên dưới, mình sẽ giải đáp nếu trong phạm vi kiến thức :D
- Tham khảo các nguồn: [Thạch Phạm Blog](http://thachpham.com), [stackoverflow](http://stackoverflow.com)

**Chúc các bạn thành công !**