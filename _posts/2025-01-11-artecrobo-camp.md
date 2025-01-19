---
title:  "體驗營- LED與直流馬達"
permalink: /aiot camp/artecrobo-led-dc-motor/
excerpt: "利用聲音感測器控制LED的燈亮與燈滅，並且利用聲音的大小控制直流馬達驅動的速度。"
header:
  teaser: assets/images/aiot_camp/20250111_led_dc_motor.png
search: false
categories: 
  - 機器人體驗營
tags:
  - AIOT
  - Python
  - 物聯網
  - 直流馬達
  - LED
sidebar:
  nav: "aiot camp"
author_profile: false
last_modified_at: 2025-01-11 14:00:00 +0800
toc: true
---

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/aiot_camp/20250111_led_dc_motor.png" alt="">
</figure> 

這是我們第一次全家去科教館參加機器人程式體驗營，此次使用的是 Artecrobo 教具與 Studuino Software 來開發，二個小時的時間，我們學習到如何用聲音感測器控制 LED 的燈亮與燈滅，並結合直流馬達組裝一台小車，也是利用聲音感測器來驅動小車的前進。

## 教具準備
* Artec 的積木
* Artecrobo 主機板
* 聲音感測器 x 1
* LED x 3

<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/aiot_camp/20250111_led_dc_motor_1.png" alt="">
  <figcaption><a href="https://www.tigergroup.com.tw/" title="Artec Robot的特色">圖片來源：Artec Robot的特色</a></figcaption>
</figure> 


## 安裝 Studuino

Studuino 的介面就跟 Scratch 一樣都是可以使用積木來編寫程式，對於還不會使用文字編程的人算是很友善的環境，它支援了 Windows、Mac、Raspberry Pi、iPad、Android、Chromebook等系統。可以依照你的作業系統環境至下面下載。

Studuino 下載連結：[https://www.artec-kk.co.jp/studuino/zh/select.php](https://www.artec-kk.co.jp/studuino/zh/select.php)

## 聲音控制LED的燈亮燈滅

目標：利用聲音感測器控制 LED 的燈亮燈滅，依聲音大小分「小、中、大」三個等級。
  * 小：亮一顆燈。
  * 中：亮二顆燈。
  * 大：亮三顆燈。

程式邏輯：主要是使用 `if ~ else` 來判斷，邏輯說明如下：

  * 將聲音感測器接在 A01 的位置。
  * 利用 Studuino 內建測試功能，測試聲音感測器的最大值，這時測到最大是 50。
  * 宣告一個變數 `value` 來收集「聲音感測器」回傳的值(這是 Owen 自己加的)。
  * 將 `value` 分成三個判斷來控制「小、中、大」三個等級。
  * 當 `value` 大於 4 就亮綠燈，將綠色的 LED 接在 A02 的位置。
  * 當 `value` 大於 20 就亮藍燈，將藍色的 LED 接在 A03 的位置。
  * 當 `value` 大於 39 就亮紅燈，將紅色的 LED 接在 A04 的位置。

```python
while True:
  value = A01聲音感測器收集的值

  if value > 4:
    A02 的 LED 燈亮
  else:  
    A02 的 LED 燈滅

  if value > 20:
    A03 的 LED 燈亮
  else:  
    A03 的 LED 燈滅

  if value > 39:
    A04 的 LED 燈亮
  else:  
    A04 的 LED 燈滅
```

## 聲音控制直流馬達前進
目標：利用聲音感測器控制直流馬達的前進或後退，再整合上述的 LED 。

程式邏輯：也是使用 `if ~ else` 來判斷，邏輯說明如下：

  * 直流馬達最大的功率值是 100，數值越大表示越快。
  * 當聲音感測器收集的值大於 4 就讓車子往前(正轉)或後退(反轉)。

這時 Owen 突發奇想，想用聲音的大小控制車子前進的速度，而直流馬達最大功率值是最大聲音感測值的兩倍，因此將 `value` 乘 2 就是馬達功率的值。

```python
while True:
  value = A01聲音感測器的值
  將直流馬達功率值設為 value*2

  if value > 4:
    將直流馬達設為正轉
    wait(0.1)
  else:
    將直流馬達設為停止

  if value > 4:
    A02 的 LED 燈亮
  else:  
    A02 的 LED 燈滅

  if value > 20:
    A03 的 LED 燈亮
  else:  
    A03 的 LED 燈滅

  if value > 39:
    A04 的 LED 燈亮
  else:  
    A04 的 LED 燈滅
```

## 心得感想

這是一場很棒的親子活動，可以了解小孩平時上課時的行為與想像力，可能對這太有興趣了，上課過程一直在忙手上的教具而忽略了老師正在說明的內容。又或許是 Owen 對這積木程式的操作與邏輯都已熟練的關係才導致這樣吧。

{% include video id="W09unS0kWqY" provider="youtube" %}

## 參考文章
1. [樂益文創股份有限公司](https://www.tigergroup.com.tw/)
2. [Studuino](https://www.artec-kk.co.jp/studuino/zh/)