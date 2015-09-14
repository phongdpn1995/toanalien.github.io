---
layout: post
title: fix lỗi load c++ nodejs
---
```text
Failed to load c++ bson extension, using pure JS version
```

### Hướng dẫn fix
#### Mac OS

```bash
xcode-select --install
```

#### Ubuntu

```bash
sudo apt-get install gcc make build-essential
```

Sau đó cập nhật lại thư viện node

```bash
rm -rf node_modules
npm cache clean
npm install
```

hoặc 

```bash
npm update
```

bài gốc : [http://stackoverflow.com/questions/21656420/failed-to-load-c-bson-extension]( http://stackoverflow.com/questions/21656420/failed-to-load-c-bson-extension)

