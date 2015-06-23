---
layout: post
title: Cài đặt Cocos2d-x trên Windows
---
### 1. Sơ lược

- Cocos2Dx là 1 Engine hỗ trợ lập trình Game đa nền tảng : Mobile ( IOS, ANDROID, Blackberry, TIZEN, WP) Window, MacOS, HTML5,.. đại loại là đủ cả.

- Ngôn ngữ để Code: Cocos2Dx hỗ trợ chủ yếu 3 ngôn ngữ: C++, Lua, Javascript.
![](/images/cocos2dx.png)
### 2. Chuẩn bị
- Tải về Cocos2dx tại trang chủ [http://www.cocos2d-x.org/download](http://www.cocos2d-x.org/download) (Tải về đúng bản cocos2d-x ko phải bản js).

- IDE (khuyên dùng VS 2012): [http://www.visualstudio.com/en-us/downloads/](http://www.visualstudio.com/en-us/downloads/)

- ANT: [http://ant.apache.org/bindownload.cgi](http://ant.apache.org/bindownload.cgi)

- Python 2.7 (ko dùng 3.4) : [https://www.python.org/download/releases/2.7.8/](https://www.python.org/download/releases/2.7.8/)

- Nền tảng Android (để build file apk cho android):
	+ ADT (kèm luôn Eclips): [https://dl.google.com/android/adt/adt-bundle-windows-x86_64-20140702.zip](https://dl.google.com/android/adt/adt-bundle-windows-x86_64-20140702.zip)

	+ NDK 9 (không dùng bản 10 vì Cocos2d-x vẫn dùng bản 9, nên với bản 10 khi build apk sẽ bị lỗi):
	[http://dl.google.com/android/ndk/android-ndk-r9d-windows-x86_64.zip](http://dl.google.com/android/ndk/android-ndk-r9d-windows-x86_64.zip)

	+ JDK: [http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
	Về cơ bản, Chỉ cần tải về Cocos2d-x và Visual studio là đã đủ để chạy các project cocos2d-x. Nhưng muốn tạo new 1 project thì cần sử dụng một script python mà Cocos2d-x có hỗ trợ, nhiệm vụ của Python là để chạy lệnh python script đó và biên dịch cho Android.

### 3. Cài đặt

- Cài đặt IDE, JDK, Python như setup phần mềm thông thường.

- Cài đặt Cocos2d-x 3.x, ANT, ADT, NDK chỉ việc giải nén vào thư mục. Nên để chung vào 1 thư mục cha cho dễ quản lý.

- Mở cmd của windows: gõ tên ổ bạn đặt các bộ cài ở trên, rồi dùng lệnh cd để đến thư mục cài đặt

ví dụ: 

```text
E:/>cd E:\ALLCocos2dx\cocos2d-x-3.2 
```
sau đó gõ 

```bash
setup.py
```

Cmd yêu cầu các đường dẫn đến các bộ cài đã chuẩn bị ở trên, ta kéo thả từng thư mục mà cmd yêu cầu vào (chú ý khi kéo thả **thêm dấu \ vào cuối đường dẫn**).

**Chú ý** tên thư mục cài đặt và đường dẫn không có dấu cách (space)

```text
+ NDK_ROOT: E:\ALLCocos2dx\NDK\ 
+ ANDROID_SDK_ROOT: E:\ALLCocos2dx\ADT\SDK\ 
+ ANT_ROOT: E:\ALLCocos2dx\ANT\bin\
```

Gõ lại setup.py lần nữa xem có lỡ bỏ qua bước nào không. Nếu cmd báo "Please restart terminal or restart computer.." thì là OK.

- Cài thêm System Varriable:
Chuột phải vào My Computer chọn Properties / chọn ở menu bên trái `Advanced System settings/Environment Variables`

Để ý phía trên là phần User Varriables, phía dưới là SystemVarriables,
Tại chỗ System, chọn path và bổ sung vào cuối:

```text
C:\Python27;C:\Python27\python.exe;E:\ALLCocos2dx\ADT\sdk\platform-tools;%ANT_HOME%/bin;
```

### 4. Làm việc với cocos2d-x

- Mở Visual studio, open project trỏ đến nơi vừa giải nén cocos2dx/build, mở file tương ứng với phiên bản Visual studio, ví dụ nếu là vs 2012 thì mở `cocos2d-win32.vc2012.sln`

- Đợi sau khi load hết solution cocos2d-x vào visual studio, chuột phải vào Solution và chọn build solution để visual studio biên dịch toàn bộ mã nguồn của cocos2d-x và các project test. Sau khi visual studio biên dịch xong toàn bộ solution cocos2d-x ta sẽ chạy thử project cpp-test: chuột phải vào project cpp-test>>Debug>>Start new instance. (Đây là project example tất cả các chức năng mà cocos2d-x có thể làm được, bạn có thể sử dụng nó tham khảo cho quá trình học cocos2d-x).
Chạy thành công nó là bạn đã hoàn thành việc cài đặt cocos2d-x và chạy project. Tiếp theo sẽ là tạo mới 1 project bằng cmd.

- Mở cmd, nếu là win8 chọn run as administrator. Gõ lệnh để tạo ra một project mới:

```text
cocos new NameProject -p com.vn.nameproject -l cpp -d E:/ALLCocos2dx/Projects
```

Đến đây là hoàn thành việc cài đặt, biên dịch, và code 1 project cocos2d-x. Ta thêm project mới này vào solution cocos2d-x để thực hiện việc biên dịch và code như bình thường.

**Chú ý:** project đã tạo ra cho các nền tảng tương ứng, chạy trên nền tảng nào thì add project tương ứng (proj.android, proj.ios,proj.blackbery,...). Chạy trên window thì add proj.win32 (hoặc 64).

Good luck !