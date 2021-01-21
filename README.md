# 軸承故障檢測訓練賽

# 資料說明
軸承有3種故障：外圈故障，內圈故障，滾珠故障，外加正常的工作狀態。如表1所示，結合軸承的3種直徑（直徑1,直徑2,直徑3）
![image](http://third.datacastle.cn/pkbigdata/master.other.img/f4ff7c74-97d3-452d-8076-3ebadf34972a.png)
training data 792筆，每筆資料是6000個按時間序列連續採樣的振動信號數值；testing data 則是528筆資料。

# 資料處理
1. 為將資料量增加，將每筆資料以300個資料點為間隔每次取3000個資料點，如此便能得到(792*10,3000)的training data
2. 將故障的種類做onehot編碼

# 模型建立
![image](https://github.com/jacky40207/DC-data-challenge/blob/main/model%20summary.png)
* CNN1D: kernel size=3 ,strides=1
* MaxPooling1D：pool_size=2
* activation function：relu
* loss function：categorical crossentropy
* optimizer：SGD
* learning rate ：0.005

# 訓練
* epochs=5000
* EarlyStopping：patience=5,monitor= val_binary accuracy
* batch size：128
# 成果
![image](https://github.com/jacky40207/DC-data-challenge/blob/main/test%E6%88%90%E6%9E%9C.png)

因為已過比賽時間，所以排名才會是第一
另外評分方式是以F1-score。
