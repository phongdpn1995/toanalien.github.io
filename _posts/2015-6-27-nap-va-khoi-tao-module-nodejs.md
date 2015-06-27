---
layout: post
title: Nạp và tạo module trong NodeJS
---
### 1. Nạp Module
- Trong NodeJS, module được liên hệ thông qua `file path` hoặc `name`. 
- Một số module thuộc về phần core được load sẵn khi khởi động node
- Những module khác bao gồm `third-party` sẽ được cài đặt thông qua `NPM` hoặc thông qua `local modules` mà bạn tự tạo.

- Để sử dụng module, bạn sử dụng hàm `require`, dạng 

```javascript
var module = require('module_name');
```

hàm require sẽ trả về kiểu đối tượng đại diện JavaScript tiếp xúc tới các module.

### 2. Xuất Module

```javascript
function Circle(x, y, r) {
	function r_squared() {
		return Math.pow(r, 2);
	}
	function area() {
		return Math.PI * r_squared();
	}
	return {
		area: area
	};
}
module.exports = Circle;
```
trong ví dụ trên, ta sử dụng hàm `module.exports` để xuất đối tượng Circle.

- Bạn có thể xuất nhiều module phức tạp, module.exports sẽ khởi tạo đối tượng rỗng, và ta thêm các thuộc tính vào đối tượng đó.


```javascript
function printA() {
console.log('A');
}
function printB() {
console.log('B');
}
function printC() {
console.log('C');
}
module.exports.printA = printA;
module.exports.printB = printB;
module.exports.pi = Math.PI;
```

*module sẽ xuất ra 2 hàm printA, printB và 1 số pi*

ví dụ gọi module đó như sau

```javascript
var myModule2 = require('./myModule2');
myModule2.printA(); // -> A
myModule2.printB(); // -> B
console.log(myModule2.pi); // -> 3.141592653589793
```


### 3. Tổng kết
- Node sử dụng CommonJS modules thay thế cho JavaScript global namespace, điều này làm cho việc quản lý code, cũng như tránh được những vấn đề bảo mật và lỗi.

- Bạn có thể sử dụng hàm `require` để load core module, third-party module hoặc module riêng của bạn từ file hoặc folder.

- Bạn có thể load `non-core module` theo đường dẫn và load module trong `node_modules` thông qua tên.

- Bạn có thể tự tạo module thông qua hàm `module.exports`

