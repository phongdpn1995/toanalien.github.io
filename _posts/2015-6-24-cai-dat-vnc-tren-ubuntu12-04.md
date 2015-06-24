---
layout: post
title: Cài đặt VNC Server trên Ubuntu 12.04
---

Bài viết dưới đây sẽ hướng dẫn bạn cách cài đặt môi trường đồ họa desktop trên server Ubuntu 12.04 và kết nối tới bằng VNC.

![](/images/vnc-ubuntu-desktop.png)

### 1. Cài gói Desktop và VNC

- Trước hết bạn phải chắc chắn vps luôn được cập nhật phần mềm mới nhất 

```bash
$ sudo apt-get update
$ sudo apt-get upgrade
```

- Ubuntu có rất nhiều gói desktop environments, trong ví dụ này sử dụng gói desktop mặc định, Unity

```bash
$ sudo apt-get install ubuntu-desktop
```

- Cài đặt VNC Server

```bash
$ sudo apt-get install vnc4server
```

### 2. Cấu hình VNC để được Full Desktop

- Trước hết phải ngắt kết nối và thoát VNC

```bash
$ vncserver -kill :1
```

- Cấu hình file xstartup trong folder `.vnc`

```bash
$ nano ~/.vnc/xstartup
```

```bash
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey 
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
```

thay đổi dòng cuối thành 

```bash
gnome-session &
```

- Lưu và khởi động vnc

```bash
$ vncserver :1
```

### 3. Cấu hình VNC khởi động khi boot

```bash
$ crontab -e
no crontab for user - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/ed
  2. /bin/nano        <---- easiest
  3. /usr/bin/vim.basic
  4. /usr/bin/vim.tiny

Choose 1-4 [2]:
```

thêm dòng `@reboot /usr/bin/vncserver :1` vào cuối file `crontab`

```text
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h dom mon dow command

@reboot /usr/bin/vncserver :1
```

- Lưu và khởi động lại VPS, thử kết nối đến bằng VNC.

Enjoy ! 