# tensorboard 筆記

## 安裝tensorboard

安裝tensorboard的版本需要在1.15版本以上才可以在pytorch使用

```python
pip install tensorboard==1.15
```

## 啟動tensorboard

logdir為tensorboard輸出數據的地方

```python
tensorboard --logdir ./run --port 8000
```

## 使用教學

### 導入tensorboard以及其他分析套件

```python
from torch.utils.tensorboard import SummaryWriter
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib import cm
```

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

```python
for i in range(10):
    x = np.random.random(1000)
    writer.add_histogram('distribution centers', x + i, i)
```

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

```python
writer.add_text('text analysis', '今天天氣真好')
```

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

```python
df = pd.DataFrame({'x':[1, 2, 3, 4], 'y':[0.7, 0.2, 0.1, 0.1]})
df = pd.DataFrame({'x':[1, 2, 3, 4], 'y':[0.7, 0.2, 0.1, 0.1]})
fig = plt.figure()
colors = cm.rainbow(np.linspace(0, 1, len(df)))
plt.bar(df['x'], df['y'], color=colors)
writer.add_figure('Bar Plot', fig)
```

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