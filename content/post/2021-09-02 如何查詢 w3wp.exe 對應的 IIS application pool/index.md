---
title: "如何查詢 w3wp.exe 對應的 IIS Application Pool"
date: 2021-09-02
categories:
    - IIS
tags:
    - IIS
    - .NET
    - windows
---

on Windows 2012 (IIS 8)

1. 選擇想要檢視的 IIS Worker Process
   ![](w3wp-1.png)

2. 切到 detail 查看該 process 的 PID
   ![](w3wp-2.png)

3. 切換到 C:\Windows\System32\inetsrv ，執行 `.\appcmd.exe list wp` 找到對應的 PID
   ![](w3wp-3.png)
