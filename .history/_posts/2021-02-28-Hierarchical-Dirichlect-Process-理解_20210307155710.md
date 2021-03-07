---
layout: post
title:  "Hierarchical Dirichlect Process 理解"
author: champion
categories: [ NLP, Nonparametric Bayesian]
image: assets/images/1.jpg
tags: [featured]
---

最近在看Hierarchical Dirichlect Process(Yee Whye TEH,Michael I. JORDAN)這篇論文，第一次接觸這樣的主題，整理了一下我自己的心得~~~

為什麼要用Hierarchical Dirichlet Process?

舉例來說，在信息檢索領域中，常常我們需要去將不同的文章去分主題，比如說今天有一篇文章"林書豪和周杰倫出新歌"，那這篇文章可能的主題是"運動"和"音樂"，這時候我們可以用DPMM去將這一個文章分成這些主題，但如果今天又有另一篇文章"王建民回國擔任投手，為國爭光"，這篇文章可能的主題是"運動"和"國家"，那又只能用另一個DPMM模型去分類，此時出現一個問題，這兩篇都有一個共同主題"運動"，但是不同的DPMM模型分類為運動，可能用不同的標籤做代表，就會出現同一標籤出現不同主題的情況，無法做到資訊共享，不然就需要將這兩篇文章合併成一篇文章，再使用DPMM去做分類。

那我會先從DP開始，然後再說明HDP

## 一.DP介紹:

DP是一個隨機過程，是由很多個Dirichlet分布所組成，首先先簡單描述一下Dirichlet分布是什麼?

假設今天我們擲一個正反兩面的不公平硬幣(Bernouli分布)，要如何算擲硬幣後正面的機率為多少?

我們會先假設先驗機率來自Beta分布，然後透過擲硬幣後得到的資料推算出後驗機率，因為共軛性(Conjugate)，後驗機率也會是Beta分布，當今天擲很多種不同硬幣時就會變成Bernouli Process。

同樣的情況推廣至多維時，變成擲一個骰子(Mutinomial分布)，此時我們的先驗機率會變成Dirchlet分布，一次模擬骰子每個面的機率，也就是Beta分布的推廣，同樣的先驗機率和後驗機率也具有共軛性(Conjugate)，後驗機率也會是Dirchlet分布，同樣當今天擲很多種不同骰子時就變成Dirichlet Process。
