
## Numpy入門 [リンク](https://colab.research.google.com/github/google/eng-edu/blob/main/ml/cc/exercises/numpy_ultraquick_tutorial.ipynb?utm_source=mlcc&utm_campaign=colab-external&utm_medium=referral&utm_content=mlcc-prework&hl=ja#scrollTo=7chgYKrC93np)

行列計算をやってくれるライブラリ

**Linear Datasetを作る**
- ``` python
    feature = np.arange(6, 21)
    print(feature)
    label = (feature * 3) + 4
    print(label)
    ``` 

- ```output
    [ 6  7  8  9 10 11 12 13 14 15 16 17 18 19 20]
    [22 25 28 31 34 37 40 43 46 49 52 55 58 61 64]
    ```

**Add Noise**
- ```python
  noise = np.random.random([15]) * 4 - 2
  print(noise)
  label = label + noise
  print(label)
  ```

- ```output
  [ 0.81884999 -1.79354715 -0.26481771  1.88115039  0.14879403  0.15454527
  1.69542393  0.32921209 -1.74477804 -1.141752    0.03896898 -0.68137445
 -0.38930163  1.41374612 -0.70017912]
[22.81884999 23.20645285 27.73518229 32.88115039 34.14879403 37.15454527
 41.69542393 43.32921209 44.25522196 47.858248   52.03896898 54.31862555
 57.61069837 62.41374612 63.29982088]
  ```

## Pandas

- DataFrames
    - pandas APIの中心的なデータフレームらしい

**表の作り方**
- ```python
  my_data = np.random.randint(low=0, high=101, size=(3, 4))
  my_column_names = ['Eleanor', 'Chidi', 'Tahani', 'Jason']
  my_dataframe = pd.DataFrame(data=my_data, columns=my_column_names)
  print(my_dataframe)
  print(my_dataframe['Eleanor'][1])
  my_dataframe['Hanet'] = my_dataframe['Tahani'] + my_dataframe['Jason']
  print(my_dataframe)
  ```

- ```output
    Eleanor Chidi Tahani Jason 
    0 74 46 44 8 
    1 43 21 58 60 
    2 94 26 2 2 
    
    43 
    
    Eleanor Chidi Tahani Jason Hanet 
    0 74 46 44 8 52 
    1 43 21 58 60 118 
    2 94 26 2 2 4
  ```



## 線形回帰

線形回帰
- 基本のモデルの式
    - $y^\prime = b + w_1x_1$
        - $b$: bias
        - $w$: weight
        - $y^\prime$: Prediction
        - $x$: Feature value
        - トレーニングではbとwを更新する
- 複数の特徴量を持たせることもできる
    - $y^\prime = b+w_1x_1+w_2x_2+w_3x_3$

損失
- 予想の精度がどの程度低いかを表す指標
- 方向ではなく距離。符号は無視。
    - 差の絶対値
    - 差の二乗
- 損失の種類
    - L1損失: 差の絶対値の合計
        - $L_1 = \sum_{i=1}^{n} |y_i - y_i^\prime|$
    - 平均絶対誤差(MAE): 差の絶対値の平均
        - $MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - y_i^\prime|$
    - L2損失: 差の二乗の合計
        - $L_2 = \sum_{i=1}^{n} (y_i - y_i^\prime)^2$
    - 平均二乗誤差(MSE): 差の二乗の平均
        - $MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - y_i^\prime)^2$
    - 平均二乗平方根誤差(RMSE):
        - $RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - y_i^\prime)^2}$
    - 二乗
        - 差が大きいと、損失はより大きくなる。
        - 差が小さい(1未満)と、損失はさらに小さくなる。
    - MAE, RMSEはモデルの予想値とスケールが一致するため、人間が解釈しやすい

