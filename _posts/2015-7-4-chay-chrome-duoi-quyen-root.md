---
layout: post
title: Chạy Chrome dưới quyền root
---
Just want to add a permanent solution to the problem:
1. Open google-chrome located in `/usr/bin` with 'gedit', 'kate' or your favorite text editor.

```bash
$ nano /usr/bin google-chrome
```

2. Add `"--user-data-dir"` (without the quotes) at the very end of the file. Mine looks like this:

```text
exec -a "$0" "$HERE/chrome" "$@" --user-data-dir
```