---
title: "所有的 Class 都要加 interface 嗎?"
date: 2022-08-07
slug: why-add-interface
draft: true
---

此範例為文字摘要的程式

```C#
interface ITextSummarizer{
    string summarizeText(string text);
}

class TextSummarizer : ITextSummarizer{
    string summarizeText(string text){
        //do something
        return "summarize Text";
    }
}
```

雖然 TextSummarizer 只有一個實作，就算之後不會有另一個實作，加上 interface 也有其他好處。


定義 interface 的優點：
* 可以測試更容易 - 
* 讓公用 API 更清晰 - 
* 有可能猜錯只需要一個實作 - 
* 同一類別可以解決兩個子問題 - 


定義 interface 的缺點：
* 需要付出更多努力 - 如果沒有 IDE 的幫忙，可能要手動多寫幾行程式碼。

