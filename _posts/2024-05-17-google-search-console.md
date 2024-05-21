---
title: Google Search Console - 超簡單教學
description: >-
  在設定完SEO後，就需要使用Google Search Console來告訴Google
author: Arthur Chen
date: 2024-05-21 13:00 +0800
categories: [Google Search Console]
tags: [Google Search Console, sitemap, SEO]
---

## 前言

由於公司上了新官網，需要讓客戶可以搜尋到，所以使用**Google Search Console**，來告訴**Google**該如何爬取我們的網站。

## Google Search Console 是什麼?

**Google Search Console**簡稱**GSC**可以知道你網站的流量、成效、曝光度等，且**GSC**有以下功能:

1. 分析網站的曝光次數、點擊次數，以及在 **Google** 搜尋中的排名。
2. 提交 **sitemap**，讓 **Google** 可以快速知道你網站的最新內容。
3. 當你的網站有問題時，會發送郵件進行通知。

## 使用情境

1. 剛上線的網站
2. 當網站有更新時想快速地讓人可以搜尋到

## Step1

先打開&ensp;`https://search.google.com/search-console/about`&ensp;並登入你的 **google** 帳號

## Step2

登入後會看到下圖，選擇右邊，輸入你的網站
![Alt](assets/img/post-img/gsc-1.png)

此時會得到一個 html 檔(要做驗證用的代表你可以存取該網站)，下載下來後將檔案放到你的主機上並按下驗證
![Alt](assets/img/post-img/gsc-2.png)

當看到下圖表示你驗證成功了，接下來按下前往資源
![Alt](assets/img/post-img/gsc-3.png)

## Step3

接下來我們需要產生**sitemap**檔，打開&ensp;`https://www.xml-sitemaps.com`&ensp;輸入你的網站後會得到一個&ensp;`sitemap.xml`&ensp;的檔案，下載並放到你的主機上。

## Step4

現在我們要提交剛剛放到主機上的**sitemap**來告訴**Google**我們的網站有哪些文章讓它來爬取，

在紅框中輸入&ensp;`sitemap.xml`&ensp;後按下驗證
![Alt](assets/img/post-img/gsc-4.png)

看到<font color="green">`成功`</font>後，接下來等大約 1 周的時間就可以了。

## 最後

這篇文章主要是分享給那些剛接觸**SEO**的人，不然辛苦的做完**SEO**後卻搜尋不到自己的網站，肯定會覺得很奇怪吧~

希望有幫助到各位，我們下次見~
