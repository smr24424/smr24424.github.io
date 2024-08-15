---
title: Nodejs爬蟲
description: >-
  Nodejs爬蟲詳細教學
author: Arthur Chen
date: 2024-06-17 11:00 +0800
categories: [Nodejs]
tags: [Nodejs, Reptile]
---

## 前言

當初會研究爬蟲是因為自己喜歡看小說，但又不想使用瀏覽器看(不想等每章的 request 時間)，於是就開始了爬蟲之旅 XD。

請<font color="red">注意!</font>爬蟲的結果請供個人使用<font color="red">不要公開或做商業用途</font>，以免觸犯法律。

## 目標

所以我們以文章標題來代替小說，**獲取 iT 幫幫忙一到五頁的文章標題並寫入 txt**。

## 步驟 1

首先創建一個全新的 node 專案並加入所需套件:

```console
mdkir reptile
cd reptile
npm init
npm i axios
npm i cheerio
```

# 步驟 2

創建一個`index.js`檔案，並引入相應套件:

```js
const axios = require("axios");
const cheerio = require("cheerio");
const fs = require("fs");
```

# 步驟 3

偽裝**Headers**這很重要，沒有偽裝可能會導致無法爬取:

```js
const headers = {
  Accept: "*/*",
  "Content-Type": "application/x-www-form-urlencoded",
  "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36"
};
```

## 步驟 4

寫爬蟲 function

```js
const GetITHelpItems = (page) => {
  return new Promise((resolve, reject) => {
    axios
      .get(`https://ithelp.ithome.com.tw/?page=${page}`, { headers })
      .then((v) => {
        var $ = cheerio.load(v.data);
        var titles = $(".tabs-content .qa-list .qa-list__title-link");
        var content = "";

        for (let i = 0; i < titles.length; i++)
          content += titles[i].children[0].data + "\n";

        resolve(content);
      })
      .catch(() => {
        reject("error");
      });
  });
};
```

## 步驟五

寫入 txt

```js
const start = async () => {
  for (let i = 1; i <= 5; i++) {
    var text = await GetITHelpItems(i);
    fs.appendFile("./a.txt", text, function (error) {});
  }
};
```

## 完整代碼

```js
const axios = require("axios");
const cheerio = require("cheerio");
const fs = require("fs");

const headers = {
  Accept: "*/*",
  "Content-Type": "application/x-www-form-urlencoded",
  "User-Agent":
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36"
};

const GetITHelpItems = (page) => {
  return new Promise((resolve, reject) => {
    axios
      .get(`https://ithelp.ithome.com.tw/?page=${page}`, { headers })
      .then((v) => {
        var $ = cheerio.load(v.data);
        var titles = $(".tabs-content .qa-list .qa-list__title-link");
        var content = "";

        for (let i = 0; i < titles.length; i++)
          content += titles[i].children[0].data + "\n";

        resolve(content);
      })
      .catch(() => {
        reject("error");
      });
  });
};

const start = async () => {
  for (let i = 1; i <= 5; i++) {
    var text = await GetITHelpItems(i);
    fs.appendFile("./a.txt", text, function (error) {});
  }
};

start();
```

## 最後

大功告成，各位請去獲取自己喜歡的文章或是圖片吧~

最後再提醒一次，<font color="red">請個人使用以免觸犯法律</font>，我們下次見~
