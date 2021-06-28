# Pабота по курсу "Нейронные сети"

## Задание 1. 
Построить графики ошибок на обучающей и тестовой выборке в процессе обучения из примера [IntroKerasTF.ipynb](https://github.com/shwars/NeuroWorkshop/blob/master/Notebooks/IntroKerasTF.ipynb)

Исходный код:
1. [MLP. Tensors (GiHub)]()

Результат построения графика ошибок и точности на обучающей и тестовой выборке в процессе обучения:
![Графики точности и ошибок](graphics_tensors/Trainig%20and%20Validation.png)

## Задание 3.
Использовать **Keras** для обучения классификатора на сети **MNIST**. При этом:
- Обратитить внимание на то, что в **Keras** заложены типовые датасеты, включая **MNIST**. Для обращения к нему достаточно пары строчек кода 
- Попробовать несколько конфигураций сети с несколькими полносвязными слоями, передаточными функциями, и разным количеством нейронов.

Исходный код:
1. [MLP. Keras. MNIST (GitHub)](MLP.%20Keras.%20MNIST.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1WsBgmp9wjBjNxjTUZ-wL8ghWv9DmUzdG?usp=sharing) 

Графики (точность на обучающей и тестовой выборках при использовании **TensorFlow(Keras)**: [MLP. Keras. MNIST (Graphics)](graphics_tf)

Результаты моделей нейронных сетей с различными параметрами при работе с набором данных **MNIST**

|№|Epoches/ Batch Size|Layers|Optimizer|Learning Rate|Loss Function|Final Train Accuracy|Final Valid Accuracy|Final Train Loss|Final Valid Loss|
|---|---|---|---|---|---|---|---|---|---|
|0|15 / 128|Flatten()<br>Dense(784, "tanh")<br>Dense(196, "sigmoid")<br>Dense(49, "relu")<br>Dense(10, "softmax").	|Adam|0.001|Categorical Crossentropy|99.83%|97.65%|0.006|0.098|
|1|15 / 128|Flatten()<br>Dense(784, "relu")<br>Dense(196, "relu")<br>Dense(49, "relu")<br>Dense(10, "softmax")	|Adam|0.001|Categorical Crossentropy|99.74%|97.67%|0.008|0.118|
|2|15 / 128|Flatten()<br>Dense(1024, "sigmoid")<br>Dense(256, "tanh")<br>Dense(10, "softmax")	|Adam|0.001|Categorical Crossentropy|99.71%|97.32%|0.011|0.099|
|3|15 / 128|Flatten()<br>Dense(784, "relu")<br>Dense(256, "sigmoid")<br>Dense(100, "tanh")<br>Dense(16, "relu")<br>Dense(10, "softmax"	|Adam|0.001|Categorical Crossentropy|99.78%|97.64%|0.008|0.111|


### Вывод
1. **Keras** - удобный инструмент для быстрого построения модели нейронной сети.
2. **MNIST** - датасет, который легко классифицируется простейшей полносвзной нейронной сетью.
3. Наилучшай точность распознавания которая достигнута: **97.67%**


---

