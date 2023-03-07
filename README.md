English | [Vietnamese](./README_vi_VN.md)

# C-in-Depth
C# in Depth

# Self-Host ASP.NET Web API 1 (C#)

This tutorial shows how to host a web API inside a console application. ASP.NET Web API does not require IIS. You can self-host a web API in your own host process.

New applications should use OWIN to self-host Web API.

### Reference
https://learn.microsoft.com/en-us/aspnet/web-api/overview/older-versions/self-host-a-web-api

### Package
`Microsoft.AspNet.WebApi.SelfHost` 5.2.9
This is a legacy package for hosting ASP.NET Web API within your own process (outside of IIS). Please use the Microsoft.AspNet.WebApi.OwinSelfHost package for new projects.
https://www.nuget.org/packages/Microsoft.AspNet.WebApi.SelfHost/