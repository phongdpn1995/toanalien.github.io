---
layout: post
title: Hướng dẫn cấu hình wifi Raspbian bằng commandline
---
Khi mới cài đặt Raspbian thì OS chưa thể kết nối mạng vì ta mới chỉ dùng cáp LAN để kết nối qua laptop, vì vậy ta cần kết nối với mạng để update và cài các gói cần thiết.

### 1. Lấy thông tin wifi

Để scan tất cả các mạng hiện tại đang có ta sử dụng câu lẹnh

```bash
$ sudo iwlist wlan0 scan
```
Thông tin hiện thị ra các mạng wifi dạng 

```text
pi@raspberrypi ~ $ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 8E:0E:E3:FC:79:F7
                    ESSID:"toanalien"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:72 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A00011010440001021049000600372A000120101100094F50504F205238323110540008000A0050F2040005
                    Quality=100/100  Signal level=100/100
          Cell 02 - Address: AC:86:74:26:50:AA
                    ESSID:"Campus NU B4-B5"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=100/100  Signal level=44/100
          Cell 03 - Address: AC:86:74:14:7A:BA
                    ESSID:"Campus NU B1-B2-B3"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:72 Mb/s
                    Quality=0/100  Signal level=47/100  
```

Ở đây ta có `ESSID:"testing"` là tên wifi. Sau đó ta cấu hình trong file `wpa_supplicant.conf`

```bash
$ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

thêm vào cuối file 

```text
network={
    ssid="tên_wifi"
    psk="mật_khẩu"
}
```

Bấm `ctrl+x` rồi `y` rồi `enter` để lưu và thoát.

Một vài giây sau ta khởi động lại adapter 

```bash
$ sudo ifdown wlan0
$ sudo ifup wlan0
```

hoặc khởi động lại


```bash
sudo reboot
```

Kiểm tra xem đã kết nối mạng được chưa bằng cách `ping google.com`

Nếu có thắc mắc gì, các bạn vui lòng để lại comment bên dưới.

Chúc vui :)

