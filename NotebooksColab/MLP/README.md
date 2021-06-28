# Многослойный персептрон
## Задание

Решить задачу классификации для датасетов **MNIST**, **FashionMNIST**, **CIFAR-10** с помощью 1, 2 и 3-слойного персептрона. Попробовать разные передаточные функции, провести сравнительную оценку решений. Решение реализовать в виде библиотеки, пригодной для решения более широкго круга задач.

[Пример](https://github.com/shwars/NeuroWorkshop/blob/master/Notebooks/IntroMyFw.ipynb)

## Отчёт по работе

Решения разделены на несколько тетрадей, для более удобного просмотра. Графики сохранены в отдельных папках


### MLP MNIST
Исходный код:
1. [MLP. MNIST (GitHub)](MLP.%20MNIST.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/11Ej63yx62mkyl2TnvwhfEQa-1IC3xOHP?usp=sharing) 

Результаты моделей нейронных сетей с различными параметрами при работе с набором данных **MNIST**:

|Layers/ Activation Functions|Loss Function|Epoches/ Batches/ Mini Batches Size|Learning Rate|Train Time|Final Train Loss|Final Train Accurancy|Final Valid Loss|Final Valid Accurancy|Best Class/ Accurancy|Worst Class/ Accurancy|
|---|---|---|---|---|---|---|---|---|---|---|
|1/softmax|cross-entropy|30/5/28|0.01|15.188 sec.|0.286|0.921|0.308|0.914|1 / 0.98 <br> 0 / 0.97 <br> 6 / 0.95|5 / 0.86 <br> 3 / 0.87 <br> 8 / 0.88|
|1/softmax|cross-entropy|30/5/28|0.05|15.361 sec.|0.243|0.932|0.287|0.920|1 / 0.98 <br> 0 / 0.97 <br> 6 / 0.96|3 / 0.87 <br> 5 / 0.87 <br> 8 / 0.87|
|1/softmax|cross-entropy|30/5/28|0.1|15.6 sec.|0.232|0.936|0.29|0.919|1 / 0.98 <br> 0 / 0.97 <br> 6 / 0.96|3 / 0.86 <br> 8 / 0.86 <br> 5 / 0.87|
|---|
|1/tanh <br> 2/softmax|cross-entropy|30/5/28|0.01|253.64 sec.|0.157|0.957|0.194|0.944|0 / 0.98 <br> 1 / 0.98 <br> 6 / 0.96|3 / 0.91 <br> 5 / 0.92 <br> 9 / 0.92|
|1/sigmoid <br> 2/softmax|cross-entropy|30/5/28|0.01|240.937 sec.|0.284|0.918|0.303|0.912|0 / 0.97 <br> 1 / 0.97 <br> 6 / 0.95|3 / 0.86 <br> 5 / 0.86 <br> 8 / 0.87|
|---|
|1/tanh <br> 2/sigmoid <br> 3/softmax|cross-entropy|30/5/28|0.01|325.371 sec.|0.192|0.945|0.221|0.935|1 / 0.98 <br> 0 / 0.97 <br> 6 / 0.96|5 / 0.88 <br> 3 / 0.90 <br> 9 / 0.91|
|1/sigmoid <br> 2/tanh <br> 3/softmax|cross-entropy|30/5/28|0.01|330.566 sec.|0.231|0.923|0.260|0.923|1 / 0.98 <br> 0 / 0.97 <br> 6 / 0.96|3 / 0.87 <br> 5 / 0.87 <br> 8 / 0.88|

Вывод:
1. На наборе данных простейшая нейронная сеть на основе персептронов способна распознать изображения с довольно высокой точностью (> 0.90).
2. При увеличении количества слоев нейронной сети, продолжительность работы возрастает.
3. Наибольшую точность распознавания получили классы изображений: **0, 1, 6**.
4. Наименее точно распознавались изображения из классов: **3, 5, 8**


Графики (точность на обучающей и тестовой выборках, матрицы ошибок): [MLP. MNIST. Graphics (GitHub)](img_mnist/)

---

### MLP Fashion MNIST
Исходный код:
1. [MLP. Fashion MNIST (GitHub)](MLP.%20Fashion%20MNIST.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SJhO3mL3Cp7NOuc7YEapo9gNOORtmBgN?usp=sharing) 

Результаты моделей нейронных сетей с различными параметрами при работе с набором данных **Fashion MNIST**:

|Layers Activation Functions|Loss Function|Epoches/ Batches/ Mini Batches Size|Learning Rate|Train Time|Final Train Loss|Final Train Accurancy|Final Valid Loss|Final Valid Accurancy|Best Class/ Accurancy|Worst Class/ Accurancy|
|---|---|---|---|---|---|---|---|---|---|---|
|1/softmax|cross-entropy|30/5/28|0.01|36.532 sec.|0.405|0.862|0.449|0.842|1 / 0.95 <br> 9 / 0.95 <br> 8 / 0.94|6 / 0.55 <br> 2 / 0.73 <br> 4 / 0.77|
|1/softmax|cross-entropy|30/5/28|0.05|28.286 sec.|0.386|0.864|0.454|0.839|1 / 0.96 <br> 8 / 0.95 <br> 9 / 0.94|2 / 0.62 <br> 6 / 0.66 <br> 4 / 0.77|
|1/softmax|cross-entropy|30/5/28|0.1|27.042 sec.|0.427|0.85|0.513|0.822|1 / 0.95 <br> 7 / 0.95 <br> 8, 9 / 0.94|2 / 0.47 <br> 6 / 0.73 <br> 4 / 0.77|
|---|
|1/tanh <br> 2/softmax|cross-entropy|30/5/28|0.01|524.747 sec.|0.292|0.896|0.362|0.872|8 / 0.97 <br> 1 / 0.96 <br> 9 / 0.95|6 / 0.62 <br> 2 / 0.78 <br> 4 / 0.82|
|1/sigmoid <br> 2/softmax|cross-entropy|30/5/28|0.01|491.887 sec.|0.395|0.861|0.435|0.843|1 / 0.95 <br> 8 / 0.95 <br> 9 / 0.94|6 / 0.53 <br> 2 / 0.73 <br> 4 / 0.78|
|---|
|1/tanh <br> 2/sigmoid <br> 3/softmax|cross-entropy|30/5/28|0.01|678.361 sec.|0.321|0.885|0.379|0.866|8 / 0.97 <br> 1 / 0.96 <br> 9 / 0.95|6 / 0.58 <br> 2 / 0.77 <br> 4 / 0.81|
|1/sigmoid <br> 2/tanh <br> 3/softmax|cross-entropy|30/5/28|0.01|705.662 sec.|0.352|0.874|0.404|0.855|8 / 0.96 <br> 1 / 0.95 <br> 7, 9 / 0.94|6 / 0.58 <br> 2 / 0.72 <br> 4 / 0.81|
|1/tanh <br> 2/tanh <br> 3/softmax|cross-entropy|30/5/28|0.01|748.174 sec.|0.251|0.909|0.338|0.88|8 / 0.97 <br> 1, 7 / 0.96 <br> 9 / 0.95|6 / 0.64 <br> 2 / 0.78 <br> 4 / 0.82|
|1/sigmoid <br> 2/sigmoid <br> 3/softmax|cross-entropy|30/5/28|0.01|655.507 sec.|0.418|0.852|0.458|0.835|1 / 0.95 <br> 8 / 0.95 <br> 9 / 0.94|6 / 0.50 <br> 2 / 0.73 <br> 4 / 0.78|

Вывод:
1. На наборе данных простейшая нейронная сеть на основе персептронов способна распознать изображения с хорошей точностью (> 0.82).
2. При увеличении количества слоев нейронной сети, продолжительность работы возрастает.
3. Наибольшую точность распознавания получили классы изображений: **1, 8, 9**.
4. Наименее точно распознавались изображения из классов: **2, 4, 6**


Графики (точность на обучающей и тестовой выборках, матрицы ошибок): [MLP. Fashion MNIST. Graphics (GitHub)](img_fashion-mnist/)

---

### CIFAR-10
Исходный код:
1. [MLP. CIFAR-10 (GitHub)](MLP.%20CIFAR-10.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SJhO3mL3Cp7NOuc7YEapo9gNOORtmBgN?usp=sharing) 

Результаты моделей нейронных сетей с различными параметрами при работе с набором данных **CIFAR-10**:

|Color Converting Method|Layers/ Activation Functions|Loss Function|Epoches/ Batches/ Mini Batches Size|Learning Rate|Train Time|Final Train Loss|Final Train Accurancy|Final Valid Loss|Final Valid Accurancy|Best Class/ Accurancy|Worst Class/ Accurancy|
|---|---|---|---|---|---|---|---|---|---|---|---|
|AVG RGB|1/softmax|cross-entropy|30/5/32|0.01|34.367 sec.|1.979|0.311|2.023|0.293|1 / 0.60|3 / 0.17 <br> 4 / 0.20 <br> 0, 2 / 0.22|
|AVG RGB|1/tanh <br> 2/softmax|cross-entropy|30/5/32|0.01|554.990 sec.|1.638|0.417|1.714|0.387|1 / 0.76 <br> 7 / 0.51|3 / 0.16 <br> 5 / 0.26 <br> 9 / 0.29|
|AVG RGB|1/tanh <br> 2/sigmoid <br> 3/softmax|cross-entropy|30/5/32|0.01|721.926 sec.|1.709|0.397|1.743|0.382|1 / 0.61 <br> 8 / 0.52|3 / 0.21 <br> 0 / 0.26 <br> 2 / 0.27|
|---|
|LUMA-REC-601|1/softmax|cross-entropy|30/5/32|0.01|34.762 sec.|1.992|0.307|2.040|0.287|1 / 0.60|3 / 0.18 <br> 0 / 0.19 <br> 4 / 0.20|
|LUMA-REC-601|1/tanh <br> 2/softmax|cross-entropy|30/5/32|0.01|589.086 sec.|1.635|0.420|1.717|0.387|1 / 0.74|3 / 0.16 <br> 5 / 0.28 <br> 9 / 0.28|
|LUMA-REC-601|1/tanh <br> 2/sigmoid <br> 3/softmax|cross-entropy|30/5/32|0.01|763.993 sec.|1.721|0.392|1.761|0.376|1 / 0.65 <br> 8 / 0.51|3 / 0.23 <br> 0 / 0.24 <br> 2 / 0.30|
|---|
|LUMA-REC-709|1/softmax|cross-entropy|30/5/32|0.01|34.863 sec.|1.991|0.307|2.038|0.285|1 / 0.60|1 / 0.60|3 / 0.17 <br> 0 / 0.19 <br> 4 / 0.21|
|LUMA-REC-709|1/tanh <br> 2/softmax|cross-entropy|30/5/32|0.01|577.535 sec.|1.630|0.421|1.714|0.390|1 / 0.75 <br> 7 / 0.5|3 / 0.17 <br> 5 / 0.29 <br> 0, 9 / 0.30|
|LUMA-REC-709|1/tanh <br> 2/sigmoid <br> 3/softmax|cross-entropy|30/5/32|0.01|913.480 sec.|1.717|0.395|1.756|0.376|1 / 0.64 <br> 8 / 0.52|3 / 0.23 <br> 0 / 0.24 <br> 5 / 0.26

Вывод:
1. На наборе данных **CIFAR-10** простейшая нейронная сеть на основе персептронов уже не способна распознать изображения с хорошей точностью (< 0.42).
2. При увеличении количества слоев нейронной сети, продолжительность работы возрастает.
3. Наибольшую точность распознавания получили классы изображений: **1, 7, 8**.
4. Наименее точно распознавались изображения из классов: **3, 0, 2, 4, 5**


Графики (точность на обучающей и тестовой выборках, матрицы ошибок): [MLP. CIFAR-10. Graphics (GitHub)](img_cifar-10/)
