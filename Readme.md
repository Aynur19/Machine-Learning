Группа: М8О-107М-20 Студент: Насыбуллин Айнур

---

## Задача бинарной классификации

Используются данные измерений погодных условий в Австралии в различных городах и населенных пунктах с 2008 по 2017 года. Источники данных: 
1. [Rain in Australia (Kaggle)](https://www.kaggle.com/jsphyg/weather-dataset-rattle-package)
2. [Rain in Australia (GitHub)](https://raw.githubusercontent.com/Aynur19/Machine-Learning/main/data/weatherAUS/weatherAUS.csv)

Краткое описание данных:

|Признак|Перевод|Тип|
|---|---|---|
|Date|Дата|Категориальный|
|Location|Локация|Категориальный|
|MinTemp|Минимальная температура|Количественный|
|MaxTemp|Максимальная температура|Количественный|
|Rainfall|Осадки|Количественный|
|Evaporation|Испарение|Количественный|
|Sunshine|Солнечность|Количественный|
|WindGustDir|Направление ветра|Категориальный|
|WindGustSpeed|Скорость порыва ветра|Количественный|
|WindDir9am|Направление ветра в 09:00|Категориальный|
|WindDir3pm|Направление ветра в 15:00|Категориальный|
|WindSpeed9am|Скорость ветра в 09:00|Количественный|
|WindSpeed3pm|Скорость ветра в 15:00|Количественный|
|Humidity9am|Влажность в 09:00|Количественный|
|Humidity3pm|Влажность в 15:00|Количественный|
|Pressure9am|Давление в 09:00|Количественный|
|Pressure3pm|Давление в 15:00|Количественный|
|Cloud9am|Облачность в 09:00|Количественный|
|Cloud3pm|Облачность в 15:00|Количественный|
|Temp9am|Температура в 09:00|Количественный|
|Temp3pm|Температура в 15:00|Количественный|
|RainToday|Дождь в день измерений|Бинарный|
|RainTomorrow|Дождь на следующий день|Бинарный|

---

Исходный код:
1. [Rain in Australia. Data Preprocessing (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/BinaryClassification/RainInAustralia/RainInAustralia_DataPreprocessing.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1kthwRTAMnztZe7AO5A_0mPbiqnvILZey/view?usp=sharing)


2. [Rain in Australia. Perceptron (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/BinaryClassification/RainInAustralia/RainInAustralia_Perceptron.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1NI1kcL5wVxl4D9PhmaLwWI8eapO5wxSW/view?usp=sharing)

3. [Rain in Australia. KNN (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/BinaryClassification_RainInAustralia_KNN.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1g_7zLYUvGR5C4Rd0UUKFk6Uh3t7fz_IR/view?usp=sharing)

4. [Rain in Australia. SVM (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/BinaryClassification/RainInAustralia/RainInAustralia_SVM.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1_MjeP75dXKlkjm_GtqBF8EAWRlppi1bd/view?usp=sharing)

5. [Rain in Australia. Logisitic Regression (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/BinaryClassification/RainInAustralia/RainInAustralia_LogisticRegression.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1T2BUG42TI6Sm4QU5Bv1ak91TSUICSEyT/view?usp=sharing)

6. [Rain in Australia. SGD (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/BinaryClassification/RainInAustralia/RainInAustralia_SGD.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/16k8OTCMCGRwaYLXFVYEh6CeO5gaOMYUP/view?usp=sharing)