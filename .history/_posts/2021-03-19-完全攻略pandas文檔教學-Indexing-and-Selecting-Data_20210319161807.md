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
    src="../assets/images/pandas/picture3.png">
</center>

還有另外一種方法可以對資料進行索引，利用屬性(".")來進行索引，比如說像下面這樣:

<script src="https://gist.github.com/rgib37190/a2bd4b3f99e802524cd278a8ebbfd3d1.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture4.png">
</center>

但是這種方法限制比較多所以還是用[  ]進行索引會比較好，限制如下:

1.索引名稱必須是valid identifier

2.索引名稱不能和python中存在的函數名稱一樣，例:df.min

3.索引名稱不能是index,major_axis,minor_axis,items,labels

上面用[  ] 和"."進行索引的方式是比較直覺的方法，但是常常我們並不事先知道資料的類型，運算上會有一些最佳化的限制，所以pandas提供了下面兩種方法:

1.使用.loc[]

這個方法會使用標籤(label)去尋找資料，總共有五種類型的標籤可輸入

(1)單一標籤，例如:'a','b'.....

(2)一個清單(list)或者陣列(array)，例如:["a","b","c"]

(3)切片標籤(slice object with labels)，例如:"a":"f"(兩側皆有包含)

(4)布林值陣列(boolean array)

(5)可調用函數(callable function)

何時會發生Error:當輸入的標籤找不到資料的時候，會出現KeyError

以下介紹幾個例子來讓大家看看

使用單一標籤

<script src="https://gist.github.com/rgib37190/3a6e33deea8258203832e7cd3e774bb9.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture4.png">
</center>

使用一個陣列去索引

<script src="https://gist.github.com/rgib37190/de6a74d17d5dc441f46c2e53d969c7ac.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture5.png">
</center>

使用切片標籤

<script src="https://gist.github.com/rgib37190/8244c1830b3db97ed437d699b6f91516.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture6.png">
</center>

使用布林值陣列

<script src="https://gist.github.com/rgib37190/e6a86678d76d3ba133952fe5b1987958.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture7.png">
</center>

使用可調用函數

<script src="https://gist.github.com/rgib37190/45e5a12c43bc792af62ee25c6e97e5aa.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture8.png">
</center>

當使用loc的切片索引的時候會將切片範圍中的切片包含進來，若索引排序過後，即使切片範圍的兩邊都沒有在資料裡，還是會把範圍內的資料選取出來，反之若沒排序，就會發生KeyError，舉個例子給大家看看

<script src="https://gist.github.com/rgib37190/8e862201b35829306fd7e9f0ba4b6871.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture9.png">
</center>

<script src="https://gist.github.com/rgib37190/99f6c0240e1377752bbd5b49fb9c36fa.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture10.png">
</center>

將Series排序後在選取

<script src="https://gist.github.com/rgib37190/6e6d82d3b9e0f1781a6e0abc5aa22d3e.js"></script>

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="../assets/images/pandas/picture11.png">
</center>

2.使用.iloc[]

這個方法會使用整數值去尋找資料，也和.loc一樣有上面這五種類型可以輸入

何時會發生Error:當輸入的整數索引超過資料的索引的時候，會出現IndexError(除了切片索引之外)，但是使用.loc時若超過並不會發生Error會把輸入範圍內包含的資料找出來
