## Использование GeoPandas для решения практических задач
---

### Суть задания:
Необходимо прочитать .csv ["geopandas_test.csv"](https://raw.githubusercontent.com/Aynur19/Machine-Learning/main/data/geopandas/geopandas_test.csv) в котором записаны геоданные (информация в заголовках) в системе координат `source` (нужно будет с помощью `pyproj` перевести в `target` для отображения на карте с помощью библиотеки `folium`). Предвартельно нужно будет преобразовать `df` в формат `geopandas`.

Нужно выяснить сколько было различных проездов автомобиля (прерывания более 0.5 секунды), визуализировать эти маршруты, визуализировать графики скорости проездов.


### Исходный код решения задачи
1. [GeoLocation_1. (GitHub)](https://github.com/Aynur19/Machine-Learning/blob/main/Notebooks/GeoLocation/GeoLocation_1.ipynb)[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1b6RcdCvVPmy7GB6MYM5vI8Sphy6v1Wyh?usp=sharing)