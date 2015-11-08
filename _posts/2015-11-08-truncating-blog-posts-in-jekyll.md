---
title: Hướng dẫn cắt post để hiển thị ngoài trang chủ Jekyll
layout: post
--- 

Tôi bắt đầu sử dụng Jekyll blog để làm blog trên Github. Jekyll chỉ hiệu quả để biến đổi nội dung markdown sang HTML, các bộ lọc cắt ngắn trong [Liquid](https://github.com/Shopify/liquid) cắt đi ở giữa thẻ `<ul>`. Tôi muốn một cách hiển thị khác, cắt trang theo ý muốn, nhưng các cách tôi tìm thấy đều khá phức tạp. Các mà tôi giới thiệu sẽ giúp bạn cắt ngắn bài viết bằng cách thêm đánh dấu (flag) để xác định phần hiển thị.

<!--break-->

Với truncate filter, nó sẽ cắt ở giữa trang HTML

{% gist b36cd12b7e15e2e46ee8 %}

thay đổi với split filter

{% gist 050c56c4cd53eec3dfa1 %}

Trong bài viết của bạn, hãy đặt flag `<!--break-->` tại nơi nào bạn muốn cắt

```text
---
layout: post
title: truncate example
---
 
Paragraph 1
 
Paragraph 2
 
<!--break-->
 
Paragraph 3
 
Paragraph 4
```

Cách trên hoạt động hoàn hảo trên Github [gh-pages](https://pages.github.com/)
