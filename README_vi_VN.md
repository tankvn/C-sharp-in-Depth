[English](./README.md) | Vietnamese

# C-in-Depth
C# in Depth

# Self-Host ASP.NET Web API 1 (C#)

ASP.NET Web API không yêu cầu IIS. Bạn có thể tự lưu trữ API Web trong quy trình máy chủ của riêng bạn.

Các ứng dụng mới nên sử dụng OWIN để tự lưu trữ API.

### Reference
https://learn.microsoft.com/vi-vn/aspnet/web-api/overview/older-versions/self-host-a-web-api

### Package
`Microsoft.AspNet.WebApi.SelfHost` 5.2.9
Đây là gói kế thừa phương pháp cũ để lưu trữ API Web ASP.NET trong quy trình process của riêng bạn (bên ngoài IIS). Vui lòng sử dụng gói Microsoft.AspNet.WebApi.OwinSelfHost cho các dự án mới.
https://www.nuget.org/packages/Microsoft.AspNet.WebApi.SelfHost/