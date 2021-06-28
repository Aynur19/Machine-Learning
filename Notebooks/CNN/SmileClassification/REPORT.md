# Отчет по лабораторной работе 
## по курсу "Искусственый интеллект"

## Нейросети для распознавания изображений


### Студенты: 
---
|ФИО|Роль в проекте|Оценка|
|---|--------------|------|
|Тверкаева Алина|Подготовил датасет|  |
|Веселов Глеб|Обучил нейросети|       |
|Насыбуллин Айнур|Написал отчёт|      |

### Результат проверки
---
|Преподаватель| Дата         |  Оценка       |
|-------------|--------------|---------------|
|Сошников Д.В.|              |               |

> *Комментарии проверяющих (обратите внимание, что более подробные комментарии возможны непосредственно в репозитории по тексту программы)*

### Тема работы
---
Необходимо подготовить набор данных и построить несколько нейросетевых классификаторов для распознавания рукописных символов. 

**Вариант рукописных символов**: **`:), :(, :|`**


### Распределение работы в команде
---
Работа в команде распределилась следующим образом:
|Работа|Тверкаева Алина|Веселов Глеб|Насыбуллин Айнур|
|------|---------------|------------|----------------|
|Написание вручную каждого символа на лисчточке по 100 раз|+|-|+|
|Сканирование полученного набора данных рукописных символов|+|-|-|
|Обрезка изображений на каждый символ размером 32*32|-|+|-|
|Отчистка изображений от линий квадратов (что не является символом)|-|+|-|
|Разработка многослойной полносвязной нейронной сети|-|-|+|
|Разработка сверточной нейронной сети|-|-|+|
|Формирование отчета по выполненой работе|+|+|+|
## Подготовка данных

Листы A4 были отсканированы в цвете с разрешением 300 dpi. Затем сканы были сохранены вспомогательной программой, совместимой со сканером.

Примеры фотографий исходных листков с рукописными символами:
![Веселые и грустные смайлики](https://github.com/MAILabs-Edu-AI/lab-neural-networks-vision-ml-cv/blob/master/source_images/happy_sad_100.jpg)

![Нейтральные смайлики](https://github.com/MAILabs-Edu-AI/lab-neural-networks-vision-ml-cv/blob/master/source_images/netral_100.jpg)

Все изображения находятся в папке [source_images](https://github.com/MAILabs-Edu-AI/lab-neural-networks-vision-ml-cv/tree/master/source_images)


Подготовка датасета осуществлялась, путем детектирования на заранее размечанном и отсканированном листе А4 вертикальных и горизонтальных линий, дальнейшего "вырезания" целевого изображения внутри образованных клеток и последующей постобработки.
 
Сложности заключались в том, что исходные изображения были разного размера, детекция линий имела погрешность, которую приходилось дообрабатывать вручную.

Для разрезания картинок был написан отдельный Jupter Notebook: [PreproccesData.ipynb](https://github.com/MAILabs-Edu-AI/lab-neural-networks-vision-ml-cv/blob/master/PreproccesData.ipynb)


Ссылка на получившийся датасет: [smiles_data](https://drive.google.com/file/d/1IgkY4ugFLgVyzTFjwskwE6lFfBdTJD2P/view?usp=sharing) - закинуто в архив

## Загрузка данных
Загрузка данных происходит в том же Jupyter Notebook, в котором идет обучение нейросети. Фрагмент кода для загрузки данных:

<pre>
    <code class="python">
if os.path.exists("smiles_img.zip") is False:
    !gdown https://drive.google.com/uc?id=1IgkY4ugFLgVyzTFjwskwE6lFfBdTJD2P
    </code>
</pre>


## Обучение нейросети

Исходный код: [CNN. Keras. Smiles (GitHub)](https://github.com/MAILabs-Edu-AI/lab-neural-networks-vision-ml-cv/blob/master/CNN.%20Keras.%20Smiles.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1JGydxxBbxSe450pSFlxw_XXfsE8_KTxL?usp=sharing)

### Полносвязная однослойная сеть
**Архитектура**
**Результаты**

### Полносвязная многослойная сеть
**Архитектура** - 
**Результаты**

|Dataset<br>Split<br>Variant|Epoches|Batch<br>Size|Layers|Optimizer|Learning<br>Rate|Loss<br>Function|Final Train<br>Accuracy|Final Valid<br>Accuracy|Final<br>Train Loss|Final<br>Valid Loss|
|---|---|---|---|---|---|---|---|---|---|---|
|0|50%/50%|30|32|Dense(1024, "relu")<br>Dense(3)      |Adam|0.001|Sparse Categorical Crossentropy|91.33%|53.85%|0.311|1.104|
|1|50%/50%|30|32|Dense(1024, "softmax")<br>Dense(3)   |Adam|0.001|Sparse Categorical Crossentropy|87.00%|57.37%|0.510|0.952|
|2|80%/20%|30|32|Dense(1024, "relu")<br>Dense(3)      |Adam|0.001|Sparse Categorical Crossentropy|92.24%|90.98%|0.236|0.298|
|3|80%/20%|30|32|Dense(1024, "softmax")<br>Dense(3)   |Adam|0.001|Sparse Categorical Crossentropy|82.86%|78.69%|0.514|0.605|
### Свёрточная сеть
**Архитектура** - двумерная сверточная нейронная сеть. Использовались вариации с применением двумерной свертки один и два раза (`Conv2D() + MaxPooling2D`). 

Такая архитектура была выбрана, так как является простым вариантом сверточной нейронной сети, обладает небольшим весом и имеет удовлетворительные метрики

**Результаты**

|Dataset<br>Split<br>Variant|Epoches|Batch<br>Size|Layers|Optimizer|Learning<br>Rate|Loss<br>Function|Final Train<br>Accuracy|Final Valid<br>Accuracy|Final<br>Train Loss|Final<br>Valid Loss|
|---|---|---|---|---|---|---|---|---|---|---|
|1|50%/50%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense (512, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|100.00%|79.17%|0.019|0.607|
|2|50%/50%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Dense (512, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|53.33%|49.68%|1.041|1.085|
|3|50%/50%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense (512, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|66.33%|50.00%|0.816|1.016|
|4|50%/50%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Dense (512, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|33.33%|31.73%|1.099|1.100|
|5|50%/50%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense(512, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|96.67%|64.42%|0.152|0.782|
|6|50%/50%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|98.67%|67.63%|0.094|0.824|
|7|50%/50%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Conv2D (512, "sigmoid")<br>MaxPooling2D (256)<br>Dense (256, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|86.33%|63.78%|0.425|0.805|
|8|50%/50%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Conv2D (512, "tanh")<br>MaxPooling2D (256)<br>Dense (256, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|99.33%|73.72%|0.052|0.742|
|9|50%/50%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Conv2D (512, "sigmoid")<br>MaxPooling2D (256)<br>Dense (256, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|56.33%|39.10%|0.948|1.107|
|10|50%/50%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Conv2D (512, "tanh")<br>MaxPooling2D (256)<br>Dense (256, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|93.67%|66.03%|0.736|0.968|
|11|80%/20%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense (512, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|99.80%|93.44%|0.037|0.131|
|12|80%/20%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Dense (512, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|53.47%|50.00%|0.976|0.974|
|13|80%/20%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense (512, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|66.12%|67.21%|0.753|0.760|
|14|80%/20%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Dense (512, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|33.67%|34.43%|1.099|1.098|
|15|80%/20%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense (512, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|97.76%|93.44%|0.131|0.179|
|16|80%/20%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|98.16%|96.72%|0.096|0.149|
|17|80%/20%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)<br>Conv2D (512, "sigmoid")<br>MaxPooling2D (256)<br>Dense (256, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|98.98%|96.72%|0.075|0.115|
|18|80%/20%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Conv2D (512, "tanh")<br>MaxPooling2D (256)<br>Dense (256, "relu")<br>Dense (3)|Adam|0.001|Sparse Categorical Crossentropy|99.59%|98.36%|0.023|0.071|
|19|80%/20%|30|32|Conv2D (1024, "tanh")<br>MaxPooling2D (512)n Conv2D (512, "sigmoid")<br>MaxPooling2D (256)<br>Dense (256, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|65.92%|65.57%|0.777|0.788|
|20|80%/20%|30|32|Conv2D (1024, "sigmoid")<br>MaxPooling2D (512)<br>Conv2D (512, "tanh")<br>MaxPooling2D (256)<br>Dense (256, "softmax")<br>Dense (3, "softmax")|Adam|0.001|Sparse Categorical Crossentropy|67.55%|67.21%|0.738|0.732|


## Выводы

Сформулируйте *содержательные* выводы по лабораторной работе. Чему он вас научила? 
Над чем заставила задуматься? В чём состояли основные сложности в работе? Насколько эффективной получилась командная работа, и какие методы для повышения эффективности командной работы вы использовали (scrum, slack, ...)?

Помните, что несодержательные выводы -
самая частая причина снижения оценки.
