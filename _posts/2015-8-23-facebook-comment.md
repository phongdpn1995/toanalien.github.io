---
layout: post
title: Hướng dẫn thêm comment facebook vào xenforo
---

Việc comment bằng facebook sẽ tiện lợi hơn nhiều vì không cần login vào xenforo, và thêm plugin này cũng dễ dàng.

- Trước hết ta cần tạo 1 app trên facebook tại [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/)
- Sau đó lấy ID của app có dạng 8976940536xxxxx
- Mở template `PAGE_CONTAINER` thêm dòng sau trước `</head>`

```html
<meta property="fb:admins" content="ID"/>
```
với `ID` là ID của app
- Mở template `ad_mesage_below` thay thế bằng dòng code 

```html
<xen:if is="{$post.position} == 0 AND !{$message.conversation_id}">
<div style="margin:15px 25px 0px;border: 1px solid #ccc; color:#fff">
            <div class="comment_fbdiv" ></div>
            <div id="fb-root"></div>
            <h4 class="threadinfohead blockhead" style="background-color: #45619D;margin:-1px;padding:10px">Bình Luận Bằng Facebook</h4>
            <div class="fb-comments" data-href="http://abc.com/{xen:link threads, $thread}" data-num-posts="10" data-width="790"></div>
</div>
</xen:if>
```

với `abc.com` là domain website của bạn.

Test: mở bất kì thread nào trong forum, kiểm tra khung comment bên dưới post 

![](/images/fbcmt.png)

Vậy là ta đã add thành công comment facebook trên xenforo.

Cảm ơn các bạn đã theo dõi ! 

