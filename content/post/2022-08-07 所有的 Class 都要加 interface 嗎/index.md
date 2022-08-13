---
title: "所有的 Class 都要加 Interface 嗎?"
date: 2022-08-07
slug: why-add-interface
categories:
    - Programming
tags:
    - Programming
---

```C#
interface ITextSummarizer{
    string summarizeText(string text);
}

class TextSummarizer : ITextSummarizer{
    string summarizeText(string text){
        //do something
        return "summarize text";
    }
}
```

雖然 TextSummarizer 只有一個實作，就算之後不會有另一個實作，加上 interface 也有其他好處。

定義 interface 的優點：

* 可以使測試更容易 - 如果要在測試期間使用 mock 或 fake 假的實作，會需要定義一個介面來執行此操作。
* 讓公用 API 更清晰 - 使用端應該或不應該使用哪些功能不會產生混淆。
* 有可能猜錯只需要一個實作 - 最初寫程式時可能確定真的不需要第二個實作，但經過一兩個月後，這個假設可能被證明是錯誤的。
* 同一類別可以解決兩個子問題 - 有時某個類別可以為兩個或多個不同的抽象層提供實作。例如 LinkedList 實作類別可以實作 List 和 Queue 介面。

定義 interface 的缺點：

* 需要付出更多努力 - 如果沒有 IDE 的幫忙，可能要手動多寫幾行程式碼。
  -> [使用 Rider 自動產生 Interface](https://www.jetbrains.com/help/rider/Refactorings__Extract_Interface.html)


---

Reference
> [Good Code, Bad Code｜寫出高品質的程式碼](https://www.tenlong.com.tw/products/9786263242128) PART 1 理論篇 - 第2章 抽象層
