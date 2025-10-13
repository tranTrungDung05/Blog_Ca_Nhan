---
title: "Header & Cookie trong HTTP"
date: 2025-10-11T16:10:00+07:00
draft: false
tags: ["HTTP", "Cookie", "Header"]
categories: ["Java & Mạng"]
author: "Trần Trung Dũng"
summary: "Giải thích chức năng của header và cookie, cách sử dụng trong giao tiếp Client-Server."
image: "/images/http-header-cookie.webp"
---
Bài viết hướng dẫn cách đọc và sử dụng HTTP header, cookie để lưu trữ thông tin, xác thực và quản lý phiên.

# Header và Cookie: Chức năng và Vai trò trong Giao tiếp Client-Server

Giao tiếp trên nền tảng Web chủ yếu dựa trên giao thức **HTTP**: hoạt động theo mô hình **Client-Server**. Để cuộc hội thoại này diễn ra hiệu quả, hai thành phần không thể thiếu là **HTTP Header** và **Cookie**. Bài viết này sẽ giải thích chi tiết chức năng và vai trò của chúng trong luồng truyền tải dữ liệu.

---

## 1. HTTP Header: Người Dẫn Đường Của Gói Tin

**HTTP Header**: là các dòng văn bản chứa siêu dữ liệu (metadata) về yêu cầu (Request) hoặc phản hồi (Response) HTTP. Chúng được đính kèm ở đầu mỗi thông điệp HTTP, trước phần nội dung chính (body).

### Chức năng và Vai trò
**Header**: không chứa dữ liệu mà người dùng cần (ví dụ: nội dung trang web), mà cung cấp thông tin cần thiết để Client và Server hiểu cách xử lý dữ liệu đó.

### Phân loại và Ví dụ
#### **Request Header** (Từ Client gửi đến Server)
Đây là thông tin mà **Client** cung cấp để giúp **Server** xử lý yêu cầu.

* **Host**: Xác định tên miền của Server mà Client muốn kết nối. Ví dụ: `Host: example.com`.
* **User-Agent**: Mô tả trình duyệt, hệ điều hành hoặc ứng dụng tạo ra yêu cầu. **Server** dùng nó để tối ưu hóa nội dung.
* **Accept-Language**: Cho biết ngôn ngữ mà Client ưu tiên hiển thị.
* **Authorization**: Chứa thông tin xác thực (ví dụ: Token), dùng để cấp quyền truy cập vào tài nguyên bảo mật.

#### **Response Header** (Từ **Server** gửi lại **Client**)
Đây là thông tin mà Server cung cấp để giúp Client hiểu và xử lý phản hồi.

* **Content-Type**: Cho biết định dạng của nội dung trong phần body. Ví dụ: `Content-Type: application/json` hoặc `text/html`.
* **Content-Length**: Kích thước của phần body tính bằng byte.
* **Server**: Thông tin về phần mềm Server đang phục vụ yêu cầu.
* **Set-Cookie**: Chỉ thị quan trọng nhất, dùng để yêu cầu Client lưu trữ Cookie.

---

## 2. Cookie: Bộ Nhớ Ngắn Hạn Của Web

**Cookie**: là các mẩu dữ liệu nhỏ do Server gửi đến và được trình duyệt (Client) lưu trữ. Mục đích chính của Cookie là giúp Server nhận diện Client trong các yêu cầu kế tiếp, khắc phục tính phi trạng thái (stateless) của HTTP.

### Cơ chế hoạt động trong Giao tiếp Client-Server
1.  **Server tạo Cookie**: Lần đầu Client gửi Request, Server tạo ra Cookie (thường chứa Session ID) và gửi nó trong Response Header bằng trường Set-Cookie.
2.  **Client lưu trữ**: Trình duyệt lưu trữ Cookie đó.
3.  **Client gửi lại Cookie**: Trong tất cả các Request tiếp theo đến cùng **Server**, trình duyệt tự động đính kèm Cookie trong Request Header bằng trường **Cookie**.
4.  **Server nhận dạng**: Server đọc *ession ID từ Cookie để nhận diện người dùng và trạng thái của họ (ví dụ: đã đăng nhập, giỏ hàng, tùy chọn cá nhân).

### Các loại Cookie phổ biến
* **Session Cookie**: Được xóa khi trình duyệt đóng, dùng cho phiên làm việc hiện tại.
* **Persistent Cookie**: Có ngày hết hạn (Expires) và được lưu trữ trên ổ đĩa **Client** cho đến khi hết hạn, dùng cho tính năng "Ghi nhớ tôi".
* **Third-Party Cookie**: Cookie do một miền khác với miền đang truy cập tạo ra, thường dùng cho quảng cáo và theo dõi người dùng.

---

## 3. Mối Liên Hệ Giữa Header và Cookie

**Cookie**: không thể tồn tại độc lập. Nó luôn được tạo ra và truyền tải thông qua HTTP Header:

* **Tạo Cookie**: Sử dụng Response Header `Set-Cookie`.
* **Truyền Cookie**: Sử dụng Request Header `Cookie`.

    Tóm lại, **Header**: cung cấp quy tắc và siêu dữ liệu cho toàn bộ giao tiếp **HTTP**, trong khi **Cookie**: là một dạng dữ liệu cụ thể, được **Header** quản lý, nhằm mục đích duy trì **trạng thái** và **nhận dạng** người dùng giữa các yêu cầu. Việc nắm vững hai thành phần này là chìa khóa để xây dựng các ứng dụng Web hiệu quả và an toàn.