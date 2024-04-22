---
title: Flutter狀態管理套件-Provider
description: >-
  Flutter狀態管理套件-Provider
author: Arthur Chen
date: 2024-04-22 14:00 +0800
categories: [Flutter]
tags: [Flutter, Provider]
---

## 前言

今天介紹的是 **Flutter 的 Provider**是一個狀態管理的套件，畢竟無論是 **Web** 還是 **App** 勢必都要有一個狀態管理套件，其好處在於可以分割**邏輯**和 **UI 介面**方便日後維護升級，且資料可以達到共享的作用。

## 優缺點

Flutter 除了 Provider 外還有許多的狀態管理套件，像是 BLoc、Redux、GetX 等等，在眾多的套件內我為何會使用 Provider?

因為 Provider 有以下優點:

1. 使用簡單不需要過多代碼，基本上只需使用 watch、read 來監聽 State 即可。
2. 是基於**InheritedWidget**上進行封裝的，穩定且不會影響效能。
3. 這是官方推薦的狀態管理套件，且也由官方進行開發和維護。

至於缺點我認為只有一個:

1. 依賴於 context，因為 context 基本上都在 widget 內才能獲取，所以沒辦法隨時隨地的去做存取。

## 安裝

```console
flutter pub add provider
```

## 創建 State 並初始化

首先創建一個 testState.dart&ensp;(在你的專案內這裡會是接收後端資料的地方)

```dart
class TestState with ChangeNotifier, DiagnosticableTreeMixin {
  int _count = 0;
  int get count => _count;

  void addCount() {
    _count += 1;
    notifyListeners();
  }
}
```

並在 main.dart 初始化

```dart
main() {
  runApp(
    MultiProvider(
      providers: [
        ChangeNotifierProvider(create: (_) => TestState()),
      ],
      child: const MyApp(),
    ),
  );
}
```

## 使用 State

使用 read 來呼叫剛剛創建的 addCount() 來對 count 做+1

```dart
 context.read<TestState>().addCount();
```

使用 watch 監聽 count，因為剛剛有使用 **\_notifyListeners()**，所以當 count 變化時畫面上會直接跟著變化

```dart
context.watch<TestState>().count;
```

## 最後

以上就是 Provider 的介紹，依照我個人的理解並用最簡單的方式來表達，相信對於剛開始接觸 Flutter 的朋友會有所幫助，我們下次見~
