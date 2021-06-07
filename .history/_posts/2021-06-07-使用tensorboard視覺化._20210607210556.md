---
layout: post
title:  "使用tensorboard視覺化"
author: champion
categories: [Pytorch, TensorBoard]
image: assets/images/tensorboard/tensorboard-logo.png
---
以前訓練模型都是硬train一發，看看模型效果好不好，但是我們如果能透過視覺化模型的權重以及loss的趨勢來判斷
模型訓練得好不好，就不會像盲人摸象一樣，無法判斷模型哪裡有問題，所以今天要來介紹tensorboard的使用~~~

# 安裝tensorboard

安裝tensorboard的版本需要在1.15版本以上才可以在pytorch使用

<script src="https://gist.github.com/rgib37190/0b41f5c323b8913870768eab5e048964.js"></script>

## 啟動tensorboard

logdir為tensorboard輸出數據的地方

<script src="https://gist.github.com/rgib37190/cbd672df689e62b338a48f831ff926c7.js"></script>

## 使用教學

### 導入tensorboard以及其他分析套件

<script src="https://gist.github.com/rgib37190/2dadaaef4fc7395569b9c29e15d17b5b.js"></script>

實例化SummaryWriter，這個的作用就是將等等要寫入的數據用特定的格式寫進指定的資料夾，

資料夾路徑預設為./run，下面的`add_scalar`函數在訓練的時候會常常用到，可以將訓練中的loss以及accuracy寫入tensorboard，後續再作分析。

<script src="https://gist.github.com/rgib37190/80dcc6b91efaecaa1df06cfa6d94a3a3.js"></script>

啟動tensorboard後就可以在SCALARS的選項中看到我們剛剛在訓練過程中的準確度和loss，路徑前面使用一樣的名字就會被歸在同一類

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/tensorboard/scalar.png">
    <br>
    <div style="color:orange; border-bottom: 0px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 1px;">(圖一)</div>
</center>

## 分布分析

使用`add_histogram`可以用來做資料分布的視覺化。

<script src="https://gist.github.com/rgib37190/7ac1507139a13949f41aa9fb884552ed.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/tensorboard/model.png">
    <br>
    <div style="color:orange; border-bottom: 0px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 1px;">(圖二)</div>
</center>


## 文字分析

使用`add_text`這個函式就可以輸出文字到tensorboard，使用方式和`add_scalar`一樣，前面參數是分類的tag，後面是要輸出的文字。

<script src="https://gist.github.com/rgib37190/8d14bcadbcc9b0eb6464c65e2e4e6d4c.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/tensorboard/text.png">
    <br>
    <div style="color:orange; border-bottom: 0px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 1px;">(圖三)</div>
</center>

## 圖片分析

常常我們會對資料去做一些視覺化，同樣也可以透過tensorboard的`add_figure`函數來實現，一樣加上分類tag，然後使用matplotlib畫圖然後輸出。

<script src="https://gist.github.com/rgib37190/3a25a7992d5908871559a4f82d7bbe36.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/tensorboard/image.png">
    <br>
    <div style="color:orange; border-bottom: 0px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 1px;">(圖四)</div>
</center>

那以上就是關於如何使用tensorboard的介紹，如果有什麼問題都可以在下面進行留言!!!如果喜歡我的文章可以幫我拍拍手哦~~~~

<div>
  <iframe
    scrolling="no"
    frameborder="0"
    style="width:100%; max-width:485px; height:240px; margin:auto; overflow:hidden; display:block;"
    src='https://button.like.co/in/embed/champion516615/button?referrer="https://rgib37190.github.io/%E5%A6%82%E4%BD%95%E5%81%9A%E5%A5%BD%E8%B3%87%E9%87%91%E7%AE%A1%E7%90%86-%E5%87%B1%E5%88%A9%E5%85%AC%E5%BC%8F%E5%91%8A%E8%A8%B4%E4%BD%A0%E7%AD%94%E6%A1%88/"'
  ></iframe>
  <div></div>
</div>