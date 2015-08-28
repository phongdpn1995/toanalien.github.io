---
layout: post
title: How to repair all databases mysql by commandline
---

```bash
$ mysqlcheck -u username -p"password" --auto-repair --check --all-databases
```
