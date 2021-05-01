# Лабораторная работа по курсу "Искусственный интеллект"
# Многослойный персептрон

| Студент | *ФИО* |
|------|------|
| Группа  | *№* |
| Оценка | *X* |
| Проверил | Сошников Д.В. |

> *Комментарии проверяющего*
### Задание

Решить задачу классификации для датасетов MNIST, FashionMNIST, CIFAR-10 с помощью 1, 2 и 3-слойного персептрона. Попробовать разные передаточные функции, провести сравнительную оценку решений. Решение реализовать в виде библиотеки, пригодной для решения более широкго круга задач.

[Пример](https://github.com/shwars/NeuroWorkshop/blob/master/Notebooks/IntroMyFw.ipynb)

Решение оформить в файле [Solution.ipynb](Solution.ipynb) 
Отчет по работе и сравнение методов пишется в этом файле после задания.
### Критерии оценки

| Сделано | Баллы |
|---------|-------|
| Реализован однослойный персептрон, классифицирующий датасет с точностью >85% | 1 |
| Реализован многослойный персептрон, классифицирующий датасет с точностью >85% | 2 |
| Реализация сделана как библиотека для обучения сетей различных конфигураций, в соответствии с примером | 1 |
| Улучшена архитектура библиотеки, отдельно вынесены алгоритмы обучения, функции потерь | 2 |
| Проведено сравнение различных гиперпараметров, таких, как передаточные функции, число нейронов в промежуточных слоях, функции потерь, с графиками обучения и матрицами неточности | 2 |
| Проведен анализ для датасета FashionMNIST | 1 |
| Проведен анализ для другого датасета с цветными картинками (CIFAR-10) | 1 |

---

## Отчёт по работе

Решения разделены на несколько тетрадей, для более удобного просмотра. Графики сохранены в отдельных папках

---

### MLP MNIST
1. [MLP. MNIST (GitHub)](https://github.com/MAILabs-Edu-AI/lab-multi-layered-perceptron-Aynur19/blob/main/MLP/MLP_MNIST.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/11Ej63yx62mkyl2TnvwhfEQa-1IC3xOHP?usp=sharing) 

Результаты моделей с различными параметрами
|Layers|Activation Functions|Loss Function|Epoches/Batches/Mini Batches Size|Learning Rate|Train Time|Final Train Loss|Final Train Accurancy|Final Valid Loss|Final Valid Accurancy|Best Class/Accurancy|Worst Class/Accurancy|
|---|---|---|---|---|---|---|---|---|---|---|---|
|1|softmax|cross-entropy|30/5/28|0.01|15.273 sec.|0.286|0.921|0.309|0.914|1/0.98|5/0.86|
|1|softmax|cross-entropy|30/5/28|0.05|15.315 sec.|0.243|0.932|0.286|0.920|1/0.98|5/0.86|
|1|softmax|cross-entropy|30/5/28|0.1|15.155 sec.|0.232|0.936|0.29|0.918|1/0.98|3/0.86|
|2|tanh/softmax|cross-entropy|30/5/28|0.01|287.234 sec.|0.155|0.957|0.191|0.944|0,1/0.98|3,5,9/0.92|
|2|sigmoid/softmax|cross-entropy|30/5/28|0.01|274.362 sec.|0.283|0.919|0.303|0.913|0,1/0.97|3,5/0.86|
|3|tanh/sigmoid/softmax|cross-entropy|30/5/28|0.01|364.068 sec.|0.187|0.946|0.216|0.937|1/0.98|5/0.89|
|3|sigmoid/tanh/softmax|cross-entropy|30/5/28|0.01|362.802 sec.|2.281|0.191|2.280|0.192|1/0.97|5,8/0.76|

Графики (точность на обучающей и тестовой выборках, матрицы ошибок): [MLP. MNIST. Graphics (GitHub)](https://github.com/MAILabs-Edu-AI/lab-multi-layered-perceptron-Aynur19/tree/main/MLP/img_mnist)

---

### MLP Fashion MNIST

1. [MLP. Fashion MNIST (GitHub)](https://github.com/MAILabs-Edu-AI/lab-multi-layered-perceptron-Aynur19/blob/main/MLP/MLP_Fashion_MNIST.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1wWFLQY32ombZ20UYH5TlODpb83-oC7Oo?usp=sharing) 

Результаты моделей с различными параметрами
|Layers|Activation Functions|Loss Function|Epoches/Batches/Mini Batches Size|Learning Rate|Train Time|Final Train Loss|Final Train Accurancy|Final Valid Loss|Final Valid Accurancy|Best Class/Accurancy|Worst Class/Accurancy|
|---|---|---|---|---|---|---|---|---|---|---|---|
|1|softmax|cross-entropy|30/5/28|0.01|27.156 sec.|0.405|0.862|0.449|0.842|9/0.96|6/0.55|
|1|softmax|cross-entropy|30/5/28|0.05|26.920 sec.|0.386|0.864|0.454|0.839|1,8,9/0.95|6/0.66|
|1|softmax|cross-entropy|30/5/28|0.10|26.879 sec.|0.426|0.850|0.512|0.823|1,7/0.95|0/0.67|
|2|tanh/softmax|cross-entropy|30/5/28|0.01|483.662 sec.|0.293|0.896|0.363|0.871|1,8/0.96|6/0.62|
|2|sigmoid/softmax|cross-entropy|30/5/28|0.01|457.980 sec.|0.395|0.861|0.435|0.843|1,8/0.95|6/0.53|
|3|tanh/sigmoid/softmax|cross-entropy|30/5/28|0.01|634.450 sec.|0.320|0.885|0.378|0.865|8/0.97|6/0.58|
|3|tanh/tanh/softmax|cross-entropy|30/5/28|0.01|638.304 sec.|0.256|0.907|0.344|0.878|8/0.97|6/0.63|
|3|sigmoid/sigmoid/softmax|cross-entropy|30/5/28|0.01|610.242 sec.|0.420|0.852|0.458|0.837|8/0.95|6/0.50|

Графики (точность на обучающей и тестовой выборках, матрицы ошибок): [MLP. Fashion MNIST. Graphics (GitHub)](https://github.com/MAILabs-Edu-AI/lab-multi-layered-perceptron-Aynur19/tree/main/MLP/img_fashion-mnist)

---

### CIFAR-10

1. [MLP. CIFAR-10 (GitHub)](https://github.com/MAILabs-Edu-AI/lab-multi-layered-perceptron-Aynur19/blob/main/MLP/MLP_CIFAR-10.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SJhO3mL3Cp7NOuc7YEapo9gNOORtmBgN?usp=sharing) 

Результаты моделей с различными параметрами
|Image Convert|Layers|Activation Functions|Loss Function|Epoches/Batches/Mini Batches Size|Learning Rate|Train Time|Final Train Loss|Final Train Accurancy|Final Valid Loss|Final Valid Accurancy|Best Class/Accurancy|Worst Class/Accurancy|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|AVG RGB|1|softmax|cross-entropy|30/5/32|0.01|35.188 sec.|1.979|0.310|2.024|0.293|1/0.60|3/0.17|
|AVG RGB|2|tanh/softmax|cross-entropy|30/5/32|0.01|474.672 sec.|1.621|0.424|1.700|0.390|1/0.76|3/0.17|
|AVG RGB|3|tanh/sigmoid/softmax|cross-entropy|30/5/32|0.01|581.418 sec.|1.708|0.400|1.741|0.383|1/0.62|3/0.22|
|LUMA-REC-601|1|softmax|cross-entropy|30/5/32|0.01|35.048 sec.|1.993|0.305|2.040|0.286|1/0.61|3/0.17|
|LUMA-REC-601|2|tanh/softmax|cross-entropy|30/5/32|0.01|486.392 sec.|1.642|0.415|1.725|0.383|1/0.77|3/0.15|
|LUMA-REC-601|3|tanh/sigmoid/softmax|cross-entropy|30/5/32|0.01|600.277 sec.|1.719|0.392|1.758|0.376|1/0.65|3/0.21|
|LUMA-REC-709|1|softmax|cross-entropy|30/5/32|0.01|35.670 sec.|1.991|0.307|2.038|0.286|1/0.60|3/0.17|
|LUMA-REC-709|2|tanh/softmax|cross-entropy|30/5/32|0.01|480.524 sec.|1.628|0.421|1.717|0.387|1/0.74|3/0.19|
|LUMA-REC-709|3|tanh/sigmoid/softmax|cross-entropy|30/5/32|0.01|603.001 sec.|1.721|0.393|1.758|0.379|1/0.65|3/0.22|

Графики (точность на обучающей и тестовой выборках, матрицы ошибок): [MLP. CIFAR-10. Graphics (GitHub)](https://github.com/MAILabs-Edu-AI/lab-multi-layered-perceptron-Aynur19/tree/main/MLP/img_cifar-10)
