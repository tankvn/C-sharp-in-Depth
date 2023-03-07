[English](./README.md) | Vietnamese

# C-in-Depth
C# in Depth

# Self-Host ASP.NET Web API 1 (C#)

ASP.NET Web API không yêu cầu IIS. Bạn có thể tự lưu trữ API Web trong quy trình máy chủ của riêng bạn.

Các ứng dụng mới nên sử dụng OWIN để tự lưu trữ API.

HTTP không chỉ để phục vụ các trang web. HTTP cũng là một nền tảng mạnh mẽ để xây dựng các API hiển thị các dịch vụ và dữ liệu. HTTP đơn giản, linh hoạt và phổ biến. Hầu hết mọi nền tảng mà bạn có thể nghĩ đến đều có thư viện HTTP, vì vậy các dịch vụ HTTP có thể tiếp cận nhiều loại khách hàng, bao gồm trình duyệt, thiết bị di động và ứng dụng máy tính để bàn truyền thống.

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
netsh http add urlacl url=http://+:8080/ user=DOMAIN\user
netsh http add urlacl url=http://+:8080/ user=BUILTIN\Administrators
netsh http add urlacl url=http://+:4488/ user=BUILTIN\Users
netsh http add urlacl url=https://+:5986/wsman/ user=NT SERVICE\WinRM
netsh http add urlacl url=https://+:3392/rdp/ user=NT SERVICE\TermService
netsh http add urlacl url=http://+:80/Temporary_Listen_Addresses/ user=\Everyone
netsh http add urlacl url=http://+:10247/apps/ user=NT AUTHORITY\Authenticated Users

netsh http show urlacl
```

trong đó machine\username là tài khoản người dùng của bạn.

Khi bạn hoàn tất việc tự lưu trữ, hãy nhớ xóa đặt chỗ:

```bat
netsh http delete urlacl url=http://+:8080/
netsh http delete urlacl url=http://+:44308/
```

### Reference
https://learn.microsoft.com/vi-vn/aspnet/web-api/overview/older-versions/self-host-a-web-api

### Package & Dependencies

#### ClientApp
`Microsoft.AspNet.WebApi.Client` 5.2.9
`Newtonsoft.Json` 6.0.4

https://www.nuget.org/packages/Microsoft.AspNet.WebApi.Client

#### SelfHost
`Microsoft.AspNet.WebApi.Client` 5.2.9
`Microsoft.AspNet.WebApi.Core` 5.2.9
`Microsoft.AspNet.WebApi.SelfHost` 5.2.9
`Newtonsoft.Json` 6.0.4
Đây là gói kế thừa phương pháp cũ để lưu trữ API Web ASP.NET trong quy trình process của riêng bạn (bên ngoài IIS). Vui lòng sử dụng gói Microsoft.AspNet.WebApi.OwinSelfHost cho các dự án mới.
https://www.nuget.org/packages/Microsoft.AspNet.WebApi.SelfHost/


# Use OWIN to Self-Host ASP.NET Web API

Lưu trữ API Web ASP.NET bằng OWIN để tự lưu trữ API Web.

Owin (Open Web Interface for Net) là một open-source, nó định nghĩa một chuẩn giao diện giữa webserver và web application. Mục đích của Owin là để tách biệt giữa server và ứng dụng, khuyến khích sự phát triển những modules đơn giản cho phát triển web trong .Net.

### Package & Dependencies
`Microsoft.AspNet.WebApi.Client` 5.2.9
`Microsoft.AspNet.WebApi.Core` 5.2.9
`Microsoft.AspNet.WebApi.Owin` 5.2.9
`Microsoft.AspNet.WebApi.OwinSelfHost` 5.2.9
`Microsoft.Owin` 2.0.2
`Microsoft.Owin.Host.HttpListener` 2.0.2
`Microsoft.Owin.Hosting` 2.0.2
`Newtonsoft.Json` 6.0.4
`Owin` 1.0

https://www.nuget.org/packages/Microsoft.AspNet.WebApi.OwinSelfHost