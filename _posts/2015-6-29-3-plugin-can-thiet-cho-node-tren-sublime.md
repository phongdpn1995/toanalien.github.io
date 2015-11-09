---
layout: post
title: 3 Plugin cần thiết cho Node và JavaScript trên Sublime Text
---
Bài viết giới thiệu 3 plugin tuyệt vời và hết sức cần thiết trên Sublime Text dành cho JavaScript và Node.

<!--break-->

### 1.JsFormat

[https://github.com/jdc0589/JsFormat](https://github.com/jdc0589/JsFormat)

JsFormat là một JavaScript plugin định dạng sử dụng dòng lệnh để định dạng từ [jsbeautifier.org](jsbeautifier.org) để format JavaScript và JSON files.

#### Chức năng
- định dạng JavaScript
- định dạng JSON
- định dạng Full file
- định dạng Selected text
- định dạng cá nhân hóa tùy chọn
- cá nhân hóa dự án với .jsbeautifyrc file

#### Sử dụng 
- `cmd+alt+f` trên OS X
- `ctrl+alt+f` trên Linux/Windows

### 2. JSHint Gutter 

[https://github.com/victorporof/Sublime-JSHint](hhttps://github.com/victorporof/Sublime-JSHint)

“JSHint is a community-driven tool to detect errors and potential problems in JavaScript code and to enforce your team’s coding conventions. It is very flexible so you can easily adjust it to your particular coding guidelines and the environment you expect your code to execute in. JSHint is open source and will always stay this way.” - JSHint

#### Sử dụng 
- `ctrl+j` trên OS X
- `alt+j` trên Linux/Windows

Nếu bạn muốn JSHint run mỗi khi lưu file, bạn cần cài đặt [SublimeOnSaveBuild](https://github.com/alexnj/SublimeOnSaveBuild) package.

- cấu hình JSHint Gutter check code ở chế độ background

```text
Ctrl + Shift + P > JsHint: Set Plugin Options
```
tìm `lint_on_edit` thành

```text
"lint_on_edit": true,
```
- cấu hình JSHint Gutter chạy code node

```text
Ctrl + Shift + P > JsHint: Set Linting Preferences
```

thay đổi cấu hình như sau 

```text
{
  "esnext": false,
  "moz": true,
  "boss": true,
  "node": true,
  "validthis": true,
  "globals": {
    "EventEmitter": true,
    "Promise": true
  }
}
```
![](/images/jshint.png)

### 3. JavaScriptNext

[https://github.com/Benvie/JavaScriptNext.tmLanguage](https://github.com/Benvie/JavaScriptNext.tmLanguage)

This plugin is a better syntax highlighter for JavaScript. Not only does it improve syntax highlighting for current ES5, it also adds syntax highlighting for new ES6 syntax such as modules, succinct methods, arrow functions, classes, and generators.

#### Sử dụng 
Bạn có thể thay đổi syntax highlighter trong `View -> Syntax -> Open all with current extension at...` 

![](/images/jssyntax.png)

trước 

![](/images/jsnextsyntax.png)

sau

### 4. Tóm lại

- 3 plugin trên hữu dụng cho JavaScript và Node developer. 
- Nếu bạn có plugin nào hay hơn, vui lòng chia sẻ chúng dưới comment để cùng nhau sử dụng.
- :)

---

