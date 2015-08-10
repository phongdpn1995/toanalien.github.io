---
layout: post
title: Fix lỗi install package trong npm trên Vagrant Ubuntu 14.04
---

Thông báo lỗi

```bash
vagrant@vagrant-ubuntu-trusty-64:/vagrant$ sudo npm install express-generator
npm ERR! Linux 3.13.0-55-generic
npm ERR! argv "/usr/bin/node" "/usr/bin/npm" "install" "express-generator"
npm ERR! node v0.12.7
npm ERR! npm  v2.11.3
npm ERR! path ../mkdirp/bin/cmd.js
npm ERR! code EPROTO
npm ERR! errno -71

npm ERR! EPROTO, symlink '../mkdirp/bin/cmd.js'
npm ERR!
npm ERR! If you need help, you may report this error at:
npm ERR!     <https://github.com/npm/npm/issues>
npm ERR! Linux 3.13.0-55-generic
npm ERR! argv "/usr/bin/node" "/usr/bin/npm" "install" "express-generator"
npm ERR! node v0.12.7
npm ERR! npm  v2.11.3
npm ERR! path npm-debug.log.8cf4dfc55c1e6af89ba84de12f39bb4a
npm ERR! code ETXTBSY
npm ERR! errno -26

npm ERR! ETXTBSY, rename 'npm-debug.log.8cf4dfc55c1e6af89ba84de12f39bb4a'
npm ERR!
npm ERR! If you need help, you may report this error at:
npm ERR!     <https://github.com/npm/npm/issues>

npm ERR! Please include the following file with any support request:
npm ERR!     /vagrant/npm-debug.log
```

Để khắc phục lỗi trên ta thêm tùy chọn `--no-bin-links` vào câu lệnh

```bash
npm install express-generator --no-bin-links
```

