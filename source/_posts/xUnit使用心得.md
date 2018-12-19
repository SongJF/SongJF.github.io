---
title: xUnit使用心得
author: SongJF
date: 2018-11-22 19:20:54
categories: .NET Core 开发
tags: 
    - 测试
    - 单元测试
    - C#
    - xUnit
---

## 在xUnit中使用DI(依赖注入)读取App配置

以读取`appsettings.json`内的`QiniuConfig`为示例

```c#
private readonly IConfigurationRoot _configuration;
private readonly IServiceProvider _serviceProvider;

private readonly IOptions<QiniuConfig> _qiniuConfig;

//构造函数
public XXXX() 
{
    // 读取Config
    var configBuilder = new ConfigurationBuilder()
        .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
        .AddEnvironmentVariables();
    _configuration = configBuilder.Build();

    //配置DI
    var services = new ServiceCollection();
    services.AddOptions();

    services.Configure<QiniuConfig>(_configuration.GetSection("QiniuConfig"));
    _serviceProvider = services.BuildServiceProvider();

    //获取配置
    _qiniuConfig = _serviceProvider.GetService<IOptions<QiniuConfig>>();
}
```