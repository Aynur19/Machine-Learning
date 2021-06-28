## Задача линейной регрессии

Используются данные моделей автомобилей марки Audi. Источники данных: 
1. [Car Price Predict (Kaggle)](https://www.kaggle.com/ersany/car-price-prediction)
2. [Car Price Predict (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/data/car_price/car_price.csv)

Источник предобработанных данны:
1. [Car Price Predict Preprocessed (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/data/car_price/car_price_prepocessed.csv)

Краткое описание данных после предобработки:
|Название|Перевод|Тип данных|Тип признака|
|---|---|---|---|
|model|Модель|Строка|Категриальный|
|body|Тип кузова|Строка|Категориальный|
|color|Цвет кузова|Строка|Категориальный|
|km|Пробег в км.|Число|Количественный|
|transmission|Тип КПП|Строка|Категориальный|
|extras|Дополнительные опции|Строка|Категориальный|
|price|Стоимость|Число|Количественный|

---

## Сравнение различных алгоритмов

### Результаты работы алгоритма SVM
**SVM params**: *C=10, cache_size=200, coef0=1.0, degree=3, epsilon=0.1, gamma='scale', kernel='poly', max_iter=-1, shrinking=True, tol=0.001, verbose=False*

|X scaling|Learning Time|Algorithm <br> accurancy on train|Cross-Validation <br> Time|R2|Variance <br> Score|Max Error|Mean Absolute <br> Error|RMSE|Median Absolute <br> Error|
|---|---|---|---|---|---|---|---|---|---|
|Not|1.11 sec.|0.39|3.87 sec.|0.358|0.361|<small>\$34 394.480</small>|\$2 699.884|\$13 219 174.077|\$2 201.854|
|StandardScaler|1.10 sec.|0.52|3.86 sec.|0.500|0.505|\$25 335.663|\$2 393.652|\$10 301 248.396|\$1 964.938|
|MinMaxScaler|1.01 sec.|0.38|3.81 sec.|0.367|0.373|\$34 583.573|\$2 673.974|\$13 045 473.850|\$2 238.552|
|MaxAbsScaler|1.02 sec.|0.38|3.79 sec.|0.367|0.373|\$34 583.573|\$2 673.974|\$13 045 473.850|\$2 238.552|
|RobustScaler|1.02 sec.|0.68|3.80 sec.|0.617|0.621|\$32 506.572|\$1 942.534|\$7 895 252.412|\$1 469.010|
|Normalizer|0.95 sec.|0.14|3.39 sec.|0.126|0.129|\$37 099.213|\$3 341.438|\$17 997 337.614|\$3 000.962|

### Результаты работы алгоритма Logistic Regression
**Logistic Regression params**: *C=1.0, class_weight=None, dual=False, fit_intercept=True, intercept_scaling=1, l1_ratio=None, max_iter=100, multi_class='auto', n_jobs=-1, penalty='l2', random_state=None, solver='lbfgs', tol=0.0001, verbose=0, warm_start=False*

|X scaling|Learning Time|Algorithm <br> accurancy on train|Cross-Validation <br> Time|R2|Variance <br> Score|Max Error|Mean Absolute <br> Error|RMSE|Median Absolute <br> Error|
|---|---|---|---|---|---|---|---|---|---|
|Not|15.81 sec.|0.01|56.31 sec.|-1.528|0.030|\$42 600.000|\$5 834.017|\$52 070 840.148|\$5 290.000|
|StandardScaler|15.68 sec.|0.31|54.91 sec.|0.497|0.500|\$25 200.000|\$2 193.131|\$10 352 395.965|\$1 490.000|
|MinMaxScaler|15.13 sec.|0.14|55.06 sec.|0.177|0.177|\$35 200.000|\$2 946.195|\$16 947 065.553|\$2 105.000|
|MaxAbsScaler|15.03 sec.|0.14|54.91 sec.|0.176|0.177|\$35 200.000|\$2 947.653|\$16 961 936.665|\$2 105.000|
|RobustScaler|15.33 sec.|0.16|50.81 sec.|0.451|0.452|\$35 200.000|\$2 260.847|\$11 307 884.165|\$1 529.000|
|Normalizer|9.39 sec.|0.02|30.54 sec.|-0.106|0.112|\$34 600.000|\$3 785.862|\$22 774 554.509|$3 500.500|


### Результаты работы алгоритма Decision Tree Regressor
**Decision Tree Regressor params:** *ccp_alpha=0.0, criterion='mse', max_depth=5, max_features='auto', max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, min_samples_leaf=1, min_samples_split=2, min_weight_fraction_leaf=0.0, presort='deprecated', random_state=42, splitter='best'*

|X scaling|Learning Time|Algorithm <br> accurancy on train|Cross-Validation <br> Time|R2|Variance <br> Score|Max Error|Mean Absolute <br> Error|RMSE|Median Absolute <br> Error|
|---|---|---|---|---|---|---|---|---|---|
|Not|0.01 sec.|0.81|0.04 sec.|0.734|0.734|\$30 361.315|\$1 598.146|\$5 484 648.943|\$1 186.769|
|StandardScaler|0.02 sec.|0.81|0.05 sec.|0.734|0.734|\$30 361.315|\$1 598.146|\$5 484 648.943|\$1 186.769|
|MinMaxScaler|0.01 sec.|0.81|0.04 sec.|0.734|0.734|\$30 361.315|\$1 598.146|\$5 484 648.943|\$1 186.769|
|MaxAbsScaler|0.01 sec.|0.81|0.05 sec.|0.734|0.734|\$30 361.315|\$1 598.146|\$5 484 648.943|\$1 186.769|
|RobustScaler|0.02 sec.|0.81|0.12 sec.|0.734|0.734|\$30 361.315|\$1 598.146|\$5 484 648.943|\$ 1186.769|
|Normalizer|0.01 sec.|0.81|0.06 sec.|0.729|0.729|\$21 675.000|\$1 635.286|\$5 591 493.814|\$1 140.812|

### Результаты работы алгоритма SGD Regressor
**SGD Regressor params:** *alpha=0.0001, average=False, early_stopping=False, epsilon=0.1, eta0=0.01, fit_intercept=True, l1_ratio=0.15, learning_rate='adaptive', loss='squared_loss', max_iter=100000, n_iter_no_change=5, penalty='l2', power_t=0.25, random_state=42, shuffle=True, tol=0.001, validation_fraction=0.1, verbose=0, warm_start=False* 

|X scaling|Learning Time|Algorithm <br> accurancy on train|Cross-Validation <br> Time|R2|Variance <br> Score|Max Error|Mean Absolute <br> Error|RMSE|Median Absolute <br> Error|
|---|---|---|---|---|---|---|---|---|---|
|Not|0.05 sec.|not valid|0.28 sec.|not valid|not valid|not valid|not valid|not valid|not valid|
|StandardScaler|0.03 sec.|not valid|0.16 sec.|not valid|not valid|not valid|not valid|not valid|not valid|
|MinMaxScaler|0.08 sec.|0.67|0.66 sec.|0.629|0.629|\$30 392.142|\$2 004.298|\$7 638 178.520|\$1 616.232|
|MaxAbsScaler|0.08 sec.|0.67|0.65 sec.|0.629|0.629|\$30 392.142|\$2 004.298|\$7 638 178.520|\$1 616.232|
|RobustScaler|42.10 sec.|0.67|119.51 sec.|0.631|0.631|\$29 485.324|\$2 002.934|\$7 591 156.166|\$1 614.058|
|Normalizer|56.07 sec.|0.24|219.32 sec.|0.204|0.205|\$37 124.820|\$3 183.322|\$16 388 351.287|\$2 928.496|

### Результаты работы алгоритма Linear Regression
|X scaling|Learning Time|Algorithm <br> accurancy on train|Cross-Validation <br> Time|R2|Variance <br> Score|Max Error|Mean Absolute <br> Error|RMSE|Median Absolute <br> Error|
|---|---|---|---|---|---|---|---|---|---|
|Not|0.03 sec.|0.67|0.04 sec.|0.629|0.630|\$29 416.336|\$2 003.556|\$7 630 586.803|\$1 611.409|
|StandardScaler|0.02 sec.|0.67|0.09 sec.|not valid|not valid|not valid|not valid|not valid|\$1 622.129|
|MinMaxScaler|0.01 sec.|0.67|0.05 sec.|not valid|not valid|not valid|not valid|not valid|\$1 615.000|
|MaxAbsScaler|0.01 sec.|0.67|0.08 sec.|not valid|not valid|not valid|not valid|not valid|\$1 624.000|
|RobustScaler|0.02 sec.|0.67|0.15 sec.|0.629|0.630|\$29 416.336|\$2 003.556|\$7 630 586.803|$1 611.409|
|Normalizer|0.01 sec.|0.25|0.04 sec.|not valid|not valid|not valid|not valid|not valid|\$2 900.350|

### Результаты работы алгоритма KNN
**KNN params:** *algorithm='brute', leaf_size=15, metric='minkowski', metric_params=None, n_jobs=-1, n_neighbors=40, p=1, weights='uniform'*

|X scaling|Learning Time|Algorithm <br> accurancy on train|Cross-Validation <br> Time|R2|Variance <br> Score|Max Error|Mean Absolute <br> Error|RMSE|Median Absolute <br> Error|
|---|---|---|---|---|---|---|---|---|---|
|Not|0.00 sec.|0.55|0.72 sec.|0.466|0.466|\$35 663.550|\$2 378.508|\$11 000 064.102|\$1 891.488|
|StandardScaler|0.01 sec.|0.57|0.69 sec.|0.531|0.534|\$31 372.725|\$2 290.944|\$9 654 486.517|\$1 864.137|
|MinMaxScaler|0.00 sec.|0.58|0.73 sec.|0.535|0.536|\$31 424.825|\$2 242.302|\$9 581 521.116|\$1 738.850|
|MaxAbsScaler|0.00 sec.|0.58|0.68 sec.|0.535|0.536|\$31 424.825|\$2 242.271|\$9 581 335.032|\$1 738.850|
|RobustScaler|0.01 sec.|0.66|0.73 sec.|0.601|0.603|\$30 187.200|\$2 042.723|\$8 212 773.219|\$1 608.188|
|Normalizer|0.00 sec.|0.77|0.69 sec.|0.692|0.700|\$32 514.800|\$1 578.972|\$6 339 702.173|\$1 075.925|


## Выводы:
1. Наиболее лучший результат показал алгоритмы дерева решений и метода ближайших соседей
2. Большинство рассмотренных алгоритмов работают лучше при отмасштабированных данных
3. Дерево решений работает одинаково как с отмасштабированными данными, так и без
4. Метод стохастического градиентного спуска не сошелся корректно на данных без масштабирования, а также на данных, отмасштабированных с дисперсией = 1 и распределением Гаусса = 0
5. Линейная регрессия (МНК) корректно сошлась на данных без масштабирования, а также на данных отмасштабированных с помощью RobustScaler
6. Результаты алгоритмов дерева решений и KNN меньше всего зависят от масштабирования данных
7. Для некоторых вариантов алгоритмы не сходились за указанное максимальное число итераций (логистическая регрессия, стохастический градиентный спуск)
8. Самым быстрым алгоритмом стал метод дерева решений

**Внимание!**: все результаты и выводы сделаны только на основании данного датасета при указанном варианте разделения данных. Последующие запуски могут дать другие результаты

---

## Исходный код:

1. [Car Price Prediction. Data Preprocessing (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/LinearRegression/CarPricePredict/CarPricePredictiction_DataPreprocessing.ipynb) 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1jnPanJsQnqo9MNNyF9IQ5hQnKO8QXMkJ?usp=sharing) - предобработка и визуализация данных. Изображения хранятся в папке `img_data_preprocessing`


2. [Car Price Prediction. KNN (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/LinearRegression/CarPricePredict/CarPricePredictiction_KNN.ipynb) 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1lxSk75YSpyobGPqyjyE18eBWTjRatobZ?usp=sharing) - применение модели KNN (метод ближайших соседей). Изображения хранятся в папке `img_knn`


2. [Car Price Prediction. Algorithms (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/LinearRegression/CarPricePredict/CarPricePredictiction_Algorithms.ipynb) 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1YDXnX0y-mpei481VZ5vVVPRsp02FpeEb?usp=sharing) - применение различных алгоритмов (МНК, SVM, KNN, стохастический градиентный спуск, логистическая регрессия, дерево решений). Графики результатов хранятся в папке `graphics`
