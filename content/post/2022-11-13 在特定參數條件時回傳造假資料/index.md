---
title: "unit test - 在特定參數條件時回傳造假資料"
date: 2022-11-13
categories:
    - Unit Test
tags:
    - Unit Test
    - NSubstitute
---

### 情境

在寫單元測試時，想判斷輸入物件的其中一個 property 是特定數值才回傳造假資料。 
可以限縮造假的範圍來提高正確性。

### 使用 NSubstitute Arg.Is\<T> 有條件的比對參數

有個 mail 物件，在寫測試時想造假特定收件人寄送的回傳值。

```C#
public class Mail
{
    public string Recipient { get; set; }
    public string Subject { get; set; }
    public List<AttachFile> Attachment { get; set; }
}
```

這時可以使用 ```Arg.Is<T>(condition)``` 裡面帶入指定條件，以此範例為收件人是 Leo 時才回傳造假的結果 ```true```。
```C#
    _mailService.Send(Arg.Is<Mail>(m => m.Recipient == "Leo")).Returns(true);
```

另外想測試是否有特定參數的呼叫 ```Received``` 一次，也可以使用 ```Arg.Is``` 去限縮條件。
```C#
    _mailService.Received(1).Send(Arg.Is<Mail>(m => m.Recipient == "Leo"));
```

### Reference
> [Argument matchers - Conditionally matching an argument](https://nsubstitute.github.io/help/argument-matchers/)