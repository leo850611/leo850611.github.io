---
title: "使用 Autofac KeyFilter Attribute 在相同介面注入不同實體"
date: 2022-07-22
slug: autofac-keyfilter-attribute
categories:
    - .NET
tags:
    - .NET
    - Autofac
---

```C#
interface IAlertService
{
   void SendAlert(string message)
}


public class SlackAlertService : IAlertService
{
    public void SendAlert(string message){}
}

public class TelegramAlertService : IAlertService
{
    public void SendAlert(string message){}
}
```

假如有個 TestAlertService 需要同時使用到 SlackAlertService 和 TelegramAlertService ，在使用 autofac 注入時因為兩個 service 都使用相同的介面，這個時候可以透過加上 KeyFilter attribute 的方式來指定所需要的實體。


KeyFilter 的使用方式：
```C#
public class TestAlertService : IAlertService
{
    public TestAlertService([KeyFilter("slack")] IAlertService slackAlert, [KeyFilter("telegram")] IAlertService slackAlert){
    ...
    }
}
```


在註冊時需要透過設定好的 key 去指定相對應的實作，以及設定哪個類別要使用 attribute filter：
```C#
builder.RegisterType<SlackAlertService>().Keyed<IAlertService>("slack");
builder.RegisterType<TelegramAlertService>().Keyed<IAlertService>("telegram");

builder.RegisterType<TestAlertService>().As<IAlertService>().WithAttributeFiltering();
```


---
參考資料：[[Autofac] resolving with attributes](https://autofac.readthedocs.io/en/latest/advanced/keyed-services.html?highlight=named#resolving-with-attributes)
