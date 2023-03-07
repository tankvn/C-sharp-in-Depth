[English](./README.md) | Vietnamese

# C-in-Depth
C# in Depth

# Self-Host ASP.NET Web API 1 (C#)

ASP.NET Web API không yêu cầu IIS. Bạn có thể tự lưu trữ API Web trong quy trình máy chủ của riêng bạn.

Các ứng dụng mới nên sử dụng OWIN để tự lưu trữ API.

Ứng dụng xác định ba hành động GET:
| URI | Mô tả |
| -- | -- | -- |
| /api/products | Lấy danh sách tất cả các sản phẩm. |
| /api/products/id | Lấy sản phẩm theo ID. |
| /api/products/?category=category | Lấy danh sách các sản phẩm theo danh mục. |

### (Optional) Add an HTTP URL Namespace Reservation

Ứng dụng này lắng nghe http://localhost:8080/. Theo mặc định, việc nghe tại một địa chỉ HTTP cụ thể yêu cầu đặc quyền của quản trị viên. Do đó, khi chạy hướng dẫn, bạn có thể gặp lỗi này: "HTTP could not register URL http://+:8080/" Có hai cách để tránh lỗi này:

- Chạy Visual Studio với quyền quản trị viên nâng cao, hoặc
- Sử dụng Netsh.exe để cấp cho tài khoản của bạn quyền đặt trước URL.

Để sử dụng Netsh.exe, hãy mở dấu nhắc lệnh với quyền quản trị viên và nhập lệnh sau: lệnh sau:

```bat
netsh http add urlacl url=http://+:8080/ user=machine\username
```

trong đó machine\username là tài khoản người dùng của bạn.

Khi bạn hoàn tất việc tự lưu trữ, hãy nhớ xóa đặt chỗ:

```bat
netsh http delete urlacl url=http://+:8080/
```

### Reference
https://learn.microsoft.com/vi-vn/aspnet/web-api/overview/older-versions/self-host-a-web-api

### Package
`Microsoft.AspNet.WebApi.Client` 5.2.9
`Microsoft.AspNet.WebApi.Core` 5.2.9
`Microsoft.AspNet.WebApi.SelfHost` 5.2.9
`Newtonsoft.Json` 6.0.4
Đây là gói kế thừa phương pháp cũ để lưu trữ API Web ASP.NET trong quy trình process của riêng bạn (bên ngoài IIS). Vui lòng sử dụng gói Microsoft.AspNet.WebApi.OwinSelfHost cho các dự án mới.
https://www.nuget.org/packages/Microsoft.AspNet.WebApi.SelfHost/