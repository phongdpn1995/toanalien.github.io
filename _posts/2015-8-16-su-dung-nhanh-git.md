---
layout: post
title: Sử dụng nhanh GIT
---
## 1. Khởi tạo kho (repository)
Ví dụ như bạn có một thư mục chứa website là `~/public_html` và bạn muốn đặt kho Git tại đó. Nếu bạn chưa có nội dung nào trong `~/public_html`, hãy tạo các thư mục và đặt một số nội dung đơn giản trong đó ví dụ như file index.html

<!--break-->

```bash
$ mkdir ~/public_html
$ cd ~/public_html
$ echo "My website is alive" >index.html
```

Để khởi tạo kho tại `~/public_html` hoặc bất kì nơi nào khác, sử dụng command:

`$ git init` Initialized empty Git repository in .git/

Git không quan tâm việc bạn bắt đầu với một thư mục rỗng hay không. Trong cả 2 trường hợp, quá trình chuyển đổi thư mục vào kho Git là như nhau.

Khi tạo kho Git bằng lệnh `git init`, một thư mục ẩn tên `.git` sẽ được tạo ra. Git đặt tất cả các thông tin về phiên bản của nó trong thư mục cao nhất `.git`.

Tất cả mọi thứ trong thư mục `~\public_html` của bạn vẫn được giữ nguyên vẹn. Git sẽ xem xét thư mục làm việc của dự án hoặc các thư mục nơi bạn thay đổi tập tin. Ngược lại, các kho ẩn bên trong `.git` được duy trì bởi Git.

## 2. Thêm file vào kho Git

Sau khi khởi tạo kho Git, kho sẽ rỗng. Để quản lý nội dung, bạn phải gửi nó vào kho. Để thêm file vào kho, ta sử dụng command:

`$ git add index.html`

*Nếu bạn có 1 thư mục chứa nhiều file, hãy sử dụng command `add all` để thêm tất cả các file trong thư mục, và dùng command `git add ..` để thêm tất cả các thư mục con. (dấu `.` đơn trong Unix là biểu thị cho thư mục đang làm việc).*

Sau khi `add`, Git biết file index.html có trong kho. Tuy nhiên Git chỉ đơn thuần là tổ chức các tập tin, một bước tạm thời để `committal`. Git tách bước `add` và `commit` để tránh sự 'bay hơi' mã nguồn (volatility). `Git add` là một bước tạm thời và có liên quan đến `git commit`, nó giúp tránh việc gây nhầm lẫn và làm hỏng mã nguồn. Bạn có thể sử dụng lệnh `add` nhiều lần và có thể `batched` (trộn) lại với nhau, giữ cho kho luôn có trạng thái ổn định.

Sử dụng command `git status`để xem trạng thái của file index.html:

`$ git status`

**output**

```bash
 # On branch master
 #
 # Initial commit
 #
 # Changes to be committed:
 # (use "git rm --cached <file>..." to unstage)
 #
 # new file: index.html
```

Thông tin output cho biết là file index.html đã được thêm vào kho cho lần Commit tiếp theo. Ngoài việc ghi lại các thay đổi của thư mục và nội dung file, Git còn lưu lại một số thông tin khác về metadata trong mỗi lần Commit. Một log đầy đủ cho 1 lần commit:

 `$ git commit -m "Initial contents of public_html" \ 
--author="Toan Vo <toanalien@gmail.com>"`

**output**

```bash
 Created initial commit 9da581d: Initial contents of public_html
 1 files changed, 1 insertions(+), 0 deletions(-)
 create mode 100644 index.html
```bash

Sau khi Commit vào kho, sử dụng lệnh `Git status` để xem trạng thái hiện tại
 `$ git status`

**output**

```bash
 # On branch master
 nothing to commit (working directory clean)
```

## 3. Cấu hình Commit Author

Trước khi Commit, bạn nên thiết lập một số thông tin cơ bản. Yêu cầu tối thiểu là Git phải biết tên bạn (your name) và email (email address). Bạn có thể thêm thông tin định danh của bạn vào mỗi lần commit. 

```bash
$ git config user.name "Toan Vo"
$ git config user.email "toanalien@gmail.com"
```
