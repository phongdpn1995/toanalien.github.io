---
layout: post
title: Hello world Nodejs on Windows
---

### 1. Cài đặt NodeJS
- download bộ cài tại [https://nodejs.org/download](https://nodejs.org/download)
- cài đặt và kiểm tra

```bash
C:\ node -v
v0.12.4
```

nếu không hiển thị phiên bản, cần kiểm tra lại biến môi trường

```text
C:\Program Files\nodejs\
```

### 2. Hello World

- tạo 1 file tên `app.js` với nội dung

```javascript
console.log('Hello World !');
```
- cd đến thư mục chứ file, gõ lệnh

```bash
C:\ node app.js

>>> Hello World !
```

- hoặc gõ trực tiếp trên cmd

```bash
node
> console.log('Hello World !');
```

Vậy ta đã cài xong NodeJS và `Hello World` thành công trên Windows.

