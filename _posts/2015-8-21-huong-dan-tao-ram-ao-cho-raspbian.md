---
layout: post
title: Hướng dẫn tạo ram ảo (Swap) cho Raspbian
---

Đối với dòng máy tính mini Raspberry Pi thì chỉ có 1gb ram, vì vậy để thực thi các ứng dụng đồ họa sẽ gây khó khăn và crash, vì vậy giải pháp tạo ram ảo (swap) bằng usb sẽ giúp trong khó khăn này.

Trước hết ta  chuẩn bị 1 usb (dung lượng tùy chọn)


### Cài đặt
- trước hết ta format usb chỉ để 1 partition
- lắp vào mainboard
- kiểm tra kết nối usb

```bash
$ sudo lsusb -t
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=dwc_otg/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/3p, 480M
        |__ Port 1: Dev 3, If 0, Class=vend., Driver=smsc95xx, 480M
```

output ra như trên là chưa có usb nào được kết nối 

```bash
$ sudo lsusb -t
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=dwc_otg/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/3p, 480M
        |__ Port 1: Dev 3, If 0, Class=vend., Driver=smsc95xx, 480M
        |__ Port 2: Dev 6, If 0, Class=stor., Driver=usb-storage, 480M
        |__ Port 3: Dev 5, If 0, Class=stor., Driver=usb-storage, 480M
```

- tìm địa chỉ usb

*câu lệnh df dùng để hiện thị các partition*

```bash
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
rootfs          3.7G  2.1G  1.4G  61% /
/dev/root       3.7G  2.1G  1.4G  61% /
devtmpfs        115M     0  115M   0% /dev
tmpfs           115M     0  115M   0% /dev/shm
tmpfs           115M  1.1M  114M   1% /run
tmpfs           115M     0  115M   0% /sys/fs/cgroup
tmpfs           115M     0  115M   0% /media
/dev/mmcblk0p1   51M   16M   36M  31% /boot

# mount
/dev/root on / type ext4 (rw,noatime,user_xattr,barrier=1,data=ordered)
devtmpfs on /dev type devtmpfs (rw,relatime,size=117396k,nr_inodes=29349,mode=755)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
..
..
```

Các thiết bị kết nối sẽ hiện thị trong `/dev/sda`

```bash
$ fdisk -l /dev/sda

Disk /dev/sda: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ae3f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1        2048    952151551   976074752    7 HPFS/NTFS/exFAT

```

ta thấy có 1 usb id **sda1**

- tạo file swap

```bash
$ dd if=/dev/sda1 of=/dev/sda1/swapfile bs=1M count=1024 
```

ví dụ trên ta tạo swap dung lượng 1GB (1MB*20124) ở /dev/sda1 (usb)

- cấu hình `dphys-swapfile` để system nhận file swap

```bash
sudo nano /etc/dphys-swapfile 
```
thay đổi thành

```text
CONF_SWAPSIZE=1024
CONF_SWAPFILE=/dev/sda1/swapfile
```

Khởi động lại swap 

```bash
$ sudo /etc/init.d/dphys-swapfile stop
$ sudo /etc/init.d/dphys-swapfile start
```

khởi động lại system sau đó dùng lệnh `top` để kiểm tra.


