---
title: "Cơ chế HTTP Request & Response"
date: 2025-10-11T15:30:00+07:00
draft: false
tags: ["HTTP", "Networking", "Web"]
categories: ["Java & Mạng"]
author: "Trần Trung Dũng"
summary: "Giải thích cơ chế GET, POST, các header và status code trong HTTP."
image: "/images/http-request.webp"
---

Bài viết giải thích cách trình duyệt gửi HTTP request và nhận response từ server, với các ví dụ minh họa trực quan.

# Cơ chế HTTP Request & Response: Từ Yêu Cầu đến Phản Hồi

Giao tiếp trên nền tảng Web dựa hoàn toàn vào **HTTP (HyperText Transfer Protocol)**, hoạt động theo mô hình **Client-Server**. Bài viết này sẽ giúp bạn hiểu cách trình duyệt gửi yêu cầu đến server và nhận phản hồi, từ đó nắm vững các loại **Request**, **Response**, **Header** và **Status Code**.

---

## 1. HTTP Request: Yêu Cầu Từ Client

**HTTP Request** là thông điệp mà Client (trình duyệt hoặc ứng dụng) gửi đến Server để yêu cầu truy xuất dữ liệu hoặc thực hiện một hành động.

### Cấu trúc Request
![CilentServer](/images/ChatGPT-Image.png)

Một HTTP Request cơ bản gồm ba phần chính:

1. **Request Line**: Chứa phương thức HTTP, đường dẫn tài nguyên và phiên bản HTTP.
    ```http
    GET /index.html HTTP/1.1
    ```
    * **GET**: Yêu cầu tài nguyên từ server.
    * **POST**: Gửi dữ liệu lên server (ví dụ: form submission).
    * **PUT, DELETE, PATCH**: Thao tác thay đổi dữ liệu trên server.
  
2. **Request Header**: Chứa metadata, giúp server hiểu yêu cầu.
    ```http
    Host: example.com
    User-Agent: Mozilla/5.0
    Accept: text/html
    ```
  
3. **Request Body** (tuỳ chọn): Chứa dữ liệu gửi đi, thường dùng với phương thức POST hoặc PUT.
    ```json
    {
      "username": "trungdung",
      "password": "123456"
    }
    ```

---

## 2. HTTP Response: Phản Hồi Từ Server

**HTTP Response** là thông điệp mà server gửi trả về cho client sau khi xử lý yêu cầu.

### Cấu trúc Response
Một HTTP Response gồm ba phần:

1. **Status Line**: Cho biết kết quả xử lý yêu cầu.
    ```http
    HTTP/1.1 200 OK
    ```
    * **200 OK**: Yêu cầu thành công.
    * **404 Not Found**: Tài nguyên không tồn tại.
    * **500 Internal Server Error**: Server gặp sự cố khi xử lý yêu cầu.

2. **Response Header**: Chứa thông tin về dữ liệu và server.
    ```http
    Content-Type: text/html
    Content-Length: 1024
    Server: Apache/2.4.41
    ```

3. **Response Body**: Chứa nội dung thực tế, ví dụ HTML, JSON hoặc hình ảnh.
    ```html
    <html>
      <body>
        <h1>Welcome to My Website</h1>
      </body>
    </html>
    ```

---

## 3. Mối Liên Hệ Giữa Request và Response

- Khi **Client** gửi **Request**, server dựa vào **Request Line** và **Header** để xác định hành động.
- Server xử lý và trả về **Response**, bao gồm **Status Code**, **Header** và **Body**.
- Toàn bộ quá trình này diễn ra trong vài mili giây, tạo cảm giác “tương tác trực tiếp” cho người dùng.

### Ví dụ minh họa
1. **Client gửi GET Request**
    ```http
    GET /about.html HTTP/1.1
    Host: example.com
    ```
2. **Server trả Response**
    ```http
    HTTP/1.1 200 OK
    Content-Type: text/html
    Content-Length: 512
    <html>
      <body>About us</body>
    </html>
    ```

---

## 4. Tóm Tắt

- **Request**: Client yêu cầu tài nguyên hoặc thực hiện thao tác, gồm Request Line, Header và Body.
- **Response**: Server phản hồi, gồm Status Line, Header và Body.
- **Header**: Chứa metadata hỗ trợ xử lý yêu cầu và phản hồi.
- **Status Code**: Cho biết kết quả của request, từ thành công (2xx), chuyển hướng (3xx), lỗi client (4xx), đến lỗi server (5xx).

Hiểu rõ cơ chế HTTP Request & Response là nền tảng quan trọng để phát triển web, debug ứng dụng, tối ưu hoá hiệu suất và bảo mật.
