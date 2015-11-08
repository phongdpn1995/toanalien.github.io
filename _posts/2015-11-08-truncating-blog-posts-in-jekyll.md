---
title: Hướng dẫn cắt post để hiển thị ngoài trang chủ Jekyll
layout: post
--- 

Tôi bắt đầu sử dụng Jekyll blog để làm blog trên Github. Jekyll chỉ hiệu quả để biến đổi nội dung markdown sang HTML, các bộ lọc cắt ngắn trong [Liquid](https://github.com/Shopify/liquid) cắt đi ở giữa thẻ `<ul>`. Tôi muốn một cách hiển thị khác, cắt trang theo ý muốn, nhưng các cách tôi tìm thấy đều khá phức tạp. Các mà tôi giới thiệu sẽ giúp bạn cắt ngắn bài viết bằng cách thêm đánh dấu (flag) để xác định phần hiển thị.

<!--break-->

Với truncate filter, nó sẽ cắt ở giữa trang HTML

```text
{% for post in site.posts limit:10 %}
	<div class="post-preview">
		<h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
		<div class="post-date">{{ post.date | date: "%B %d, %Y" }}</div>
		{% if post.content.size > 2000 %}
			{{ post.content | truncatewords: 300 }} <!-- bad! content gives you rendered html and you will truncate in the middle of a node -->
			<a href="{{ post.url }}">read more</a>
		{% else %}
			{{ post.content }}
		{% endif %}
	</div>
	<hr>
{% endfor %}
```

thay đổi với split filter

```text
{% for post in site.posts limit:10 %}
	<div class="post-preview">
		<h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
		<div class="post-date">{{ post.date | date: "%B %d, %Y" }}</div>
		{{ post.content | split:'<!--break-->' | first }}
		{% if post.content contains '<!--break-->' %}
			<a href="{{ post.url }}">read more</a>
		{% endif %}
	</div>
	<hr>
{% endfor %}
```

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

