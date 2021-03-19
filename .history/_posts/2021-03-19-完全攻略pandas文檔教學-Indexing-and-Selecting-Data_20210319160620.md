---
layout: post
title:  "完全攻略pandas文檔教學 Indexing and Selecting Data"
author: champion
categories: [Pandas]
image: assets/images/pandas/pandas.png
---

在使用pandas的時候最常使用到的就是索引(index)，常常需要在資料表裡找出需要的資料，這時候就需要索引來幫助我們找出我們所需要的資料，在看完文檔後，整理了一下索引的使用方法

可使用的資料類型:Series,DataFrame,Panel

基本的索引:

我們使用[  ]來進行索引，就像下面這樣，左圖為我們建立的資料表，右圖為選取A欄位的結果

<script src="https://gist.github.com/rgib37190/3457fe610772401a8ff4e4ec98205e29.js"></script>

<center class="half">
    <img src="../assets/images/pandas/picture1.png" width="350"/><img src="../assets/images/pandas/picture2.png" width="350"/>
</center>

或者可以一次傳入多個欄位

<script src="https://gist.github.com/rgib37190/3acdba264ea463bbf6cc4b698757be24.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/DataBase/picture3.png">
    <br>
    <div style="color:orange; border-bottom: 0px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 1px;">(圖二)</div>
</center>

還有另外一種方法可以對資料進行索引，利用屬性(".")來進行索引，比如說像下面這樣:

<script src="https://gist.github.com/rgib37190/a2bd4b3f99e802524cd278a8ebbfd3d1.js"></script>