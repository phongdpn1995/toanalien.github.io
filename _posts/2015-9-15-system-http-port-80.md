---
layout: post
title: Lỗi port 80 khi chạy ứng dụng node
---

![](/images/system-http-port-80.png)

Cách fix:

1. Tải CurrPorts tại [http://www.nirsoft.net/utils/cports.html](http://www.nirsoft.net/utils/cports.html) để xem services nào đang chiếm port sau đó mở tasks manager để kill

2. Thông thường là services http của windows hoặc apache, ta dùng lệnh sau để kill services

```bash
NET stop HTTP
```

**lưu ý**: mở cmd trong chế độ administrator 

![](/images/kill-http.png)

