---
title: "所有程式都要加 interface 嗎?"
date: 2022-08-07
slug: why-add-interface
draft: true
---
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

雖然TextSummarizer只有一個實作，就算之後不會有另一個實作，加上interface也是有其他好處:
