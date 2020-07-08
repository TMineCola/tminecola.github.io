---
title: "不靠海的校園實境解謎活動 - Lost"
date: 2020-07-07T18:00:00+08:00
modified: 2020-07-08T12:00:00+08:00
thumbnailImage: "/images/2020/07/07/lost-logo.jpg"
thumbnailImagePosition: left
tags:
- MOLi Activity
- Alternate Reality Game
keywords:
- MOLi
- Lost
- ARG
showPagination: true
---

簡單來說這是一款「以國立暨南國際大學校園為背景的實境解謎遊戲」，趁著記憶還沒被抹去之前回顧一下這個活動，順便把一些心得與遺憾都記錄下來。

<!--more-->

# 活動

## 起源

這個活動起源於 [@UncleHanWei](https://github.com/UncleHanWei) ，一位目前仍常駐在 MOLi 實驗室的地頭蛇，完整的來龍去脈已經記不得了，依稀是有剩餘的經費想要趁還有人想舉辦活動的時候趕緊把他花掉，再依照我們的相處模式應該會長這樣：

{{< blockquote @UncleHanWei >}}
不然就來辦場解謎啊
{{< /blockquote >}}
{{< blockquote @MineCola >}}
來啊！辦啊！
{{< /blockquote >}}

諸如此類的，總之 MOLi 一直以來的風格大概也都像是這樣，說幹就幹，或許這是一種文化？還是前輩們的傳承？無論如何展開了一個奇妙的活動，而合作夥伴 MysC(推理同好社) 則是因為有認識的學妹過去在裡面擔任社長，也跟這個活動的內容有著一定的相關性，所以經過一番接洽就拉進來了。

## 概念

參考了各種大大小小的解謎，涵蓋了實境解謎、密室逃脫、解謎網頁與老高的影片，我們想著要搞出一個結合網頁技術的實境解謎遊戲，結合故事主題能夠來個虛擬與實體的整合，玩家必須穿梭於「虛擬(網頁)」及「實體(校園)」之間來串連線索並且解開故事的謎底。

---

# 關於故事

## 簡介

事情從收到一封神秘的信開始，基於好奇，各位決定踏入尋找答案的旅途，意外的與即將消失的 “王翰同” 產生了連結，揭開了這個世界運作的面紗，並從旁拯救了他。

## 關卡

整個故事分成七段，每一段都有其對應的謎題與線索，以及最開始的楔子與最後的結局，文章中只會提到一小部分題目及構想方式，而詳細的故事與解謎流程可以參考：[釋出的活動解答](https://hackmd.io/@minecola/S1lOgHGAV)。

### 報名關卡

一開始活動資訊公布在學校的臉書社團中，而並未提供任何報名連結，我們用一個拼圖的概念，將一張報名資訊切割成九塊拼圖，並且交由九個工作人員將頭貼更換成其中某一塊，當初一開始構想是讓九位隨機在活動資訊文下方留言，但又怕太困難沒有人願意報名，因此用了一招類似 Link List 的方法：互相標記，透過互相標記的方法讓大家注意到我們的頭貼，因而解開報名資訊，結果發現太簡單了...真是失策。

![報名全圖](/images/2020/07/07/lost-logo.jpg)

### 楔子

活動開始當天的零時零分會透過學校 SMTP Server 來發送郵件，包含楔子和第一道謎題，而這個部分很有趣，當初會使用 Email 來做為管道是因為...去年的暨大 SMTP Server 25 Port 是只要學校內網都可以隨便發送的，然後今年測試是有鎖起來了，蠻有趣的一個體驗，而且學校的 Server 針對大量的發信還是會擋，當時我是用 Random 等待時間的方式去發送，現在想起來應該做個簡單的 Queue 就能解決。

![初始活動郵件](/images/2020/07/07/mail.png)

### 第一關

前面楔子解完會得到一個 地點(圖片解) 和 教室編號(連結解)，會引導至學生活動中心 403，而這個 403 當初想到與 HTTP Code 的 Forbidden 代號有所關聯，就復刻了一個 Nginx 自帶的 403 頁面並且加上反白文字來提示玩家這並不是原生的頁面，而重點是在於這個地點可以獲得一張精心設計的偽學生證卡片。

為了避免疑慮我們有特別讓卡片可以識別是非官方學生證，而這張卡片不是隨便一張厚紙板或塑膠片，是貨真價實 Mifare 白卡，當初設計上希望可以透過一些 RFID 機制去辨識讀寫資訊在卡片裡頭，後來因為開發時程趕不上只好捨棄，如果有人手上還有這張白卡的話，可以拿去寫入學生證 UID (對！沒錯，這張是 Sector 0 可寫入的版本)，這樣就可以出入校園和圖書館了 XD

如果未來還有舉辦下一場的話，認真覺得應該可以用 RFID 的機制來辨識組別，以及在裡面寫入一些資訊來防止跨組別的作弊，再加上 A/B 鑰及特殊寫入內容來檢查是否有被暴力竄改就十分安全了。

![獲得卡片](/images/2020/07/07/card.jpg)

### 第四關

主要會想要拿出來講是因為這關裡的一個木製盒子，裡面的 QR Code 分成正反兩面，還蠻好辨識的，一樣是採用拼圖的方式。然而這關有一個 BUG 在於我們使用的廉價爛鎖是可以透過鬆緊度來猜出密碼的，甚至有組別是在校園亂晃找到直接暴力破解，跳過第三關，後來聽到的心得是：「當個物理型駭客真香。」

還有一點是我一定要特別拿來講的，也就是這個木製盒子是純手工，出自 UncleHanWei 之手，從木板、切割、磨平、黏著到防水漆都是他親手完成的，極為厲害。

![木製盒子](/images/2020/07/07/box.jpg)

### 第五關、第六關

這兩關都是致敬老高而生的關卡，給我們靈感的原始影片附後面，主要是參考裡面共濟會密碼以及圖片隱碼術，其實後來也有玩家發覺我們是老高粉絲，我只能說：「我們都是五歲抬頭團的一員，萬歲！」。

{{< youtube _QYeqm3V3hQ >}}

---

# 結語與心得

整個活動因為在短短兩三個月中需要歷經企劃、題目構想、實作、測試及修改，而導致沒有結合一些比較具有技術深度的功能，感覺使用者體驗降低了不少，不過整體的活動回饋是好的，其實在 [Hitcon - HackDoor](https://hitcon.org/2019/hackdoor/) 與台科學生會舉辦的解謎活動中有很多靈感，包含利用 Wifi 才能接觸到一些 IoT 裝置或頁面，以及可以透過藍芽或手機 APP 去定位及互相溝通等，希望在未來這個活動能繼續延續下去，讓大家可以專研技術同時又實務應用到活動上，比起這次沒有 Database 的後端，還能夠再學習到更多的東西，加油！

目前 Lost 2 是在已經規劃完的狀態，不過因為開發時程太趕加上人力吃緊，還是跟 UncleHanWei 提出延期的要求，希望 Lost 2 舉辦的時候，是以一個完整且我們自己都很滿意的狀態下來舉辦，也希望這次能夠有更多人參與，結合資訊、文學、解謎、團隊合作與小組抗衡帶給大家與市面上的實境解謎截然不同的體驗。