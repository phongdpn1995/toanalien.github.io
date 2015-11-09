---
layout: post
title: Upgrade NodeJS via NPM
---

I was recently installing a utility via NPM when I learned that my version of Node.js itself was out of date.  No worries -- simply upgrade my Node.js install and move forward.  Of course I could just hit nodejs.org and get the new image, but figured there had to be an easier way. 

<!--break-->

It turns out there is -- you can upgrade your local Node.js with NPM:

```bash
$ sudo npm cache clean -f
$ sudo npm install -g n
$ sudo n stable
```
The n package represents a Node helper, and running the last command upgrades node to the latest stable version.  Instead of using "stable", you could specify a desired version:

```bash
$ sudo n 0.12.7
```

Once your install is complete, you can confirm you version with another command:

node -v
It's quite nice that you can upgrade Node.js right from npm;  it's like Inception...or something.