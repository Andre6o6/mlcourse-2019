# mlcourse-2019
## Задание 1
Датасет — Facebook Comment Volume Dataset.

Предсказать, сколько комментариев наберёт пост. Задача предполагает реализацию градиентного спуска и подсчёта метрик оценки качества модели. Можно использовать линейную алгебру, всякую другую математику готовую в либах.

Этапы решения:
— нормировка значений фичей;
— кросс-валидация по пяти фолдам и обучение линейной регрессии;
— подсчёт R^2 (коэффициента детерминации) и RMSE.

Результаты можно оформить в виде следующей таблицы. T1,..T5 — фолды, E — среднее, STD — дисперсия, R^2/RMSE-test — значение соответствующей метрики на тестовой выборке, -train — на обучающей выборке, f0,..fn — значимость признаков (они же переменные, они же фичи).

[**Код** ](Task1.ipynb)

## Задание 2
Предлагаю взять в качестве тестового датасет от [Netflix Prize](https://www.kaggle.com/netflix-inc/netflix-prize-data).

Собственно задача - есть матрица рейтингов User-Item, по кросс-валидации бьем её на фолды, 
затем пытаемся предсказать скрытые рейтинги. Качество проверяем по RMSE, только для тех точек в которых прогноз есть.
Используем [факторизационную машину 2-го порядка](https://www.csie.ntu.edu.tw/~b97053/paper/Rendle2010FM.pdf) с квадратичной функцией потерь (аналогично линейной регрессии).

[**Код** ](Task2.ipynb)

## Задание 3

Нужно
1) Написать свой маленький, но собственный фреймворк для обучения нейросетей, должны быть реализованы следующие слои:
Полносвязный(Dense, FullyConnected, Linear — вариации названия этого слоя), Dropout, несколько видов активаций — Relu, LeakyRelu, SoftPlus(Апроксимация Relu логарифмой log(1+e^x)), логистическую сигмоиду и softmax и logsoftmax(в комбинации с кроссэнтропией сильно улучшит сходимость, информация об этом есть по приложенной для вдохновения ссылке).
А также как минимум 2 функции потерь — mse и crossentropy(для многоклассовой классификации).

* [Заготовки слоев (их больше, чем надо)](https://github.com/yandexdataschool/Practical_DL/blob/fall18/_under_construction/homework01/homework_modules.ipynb)
* [Обучение сети на данных слоях (автоэнкодер реализовывать не нужно)](https://github.com/yandexdataschool/Practical_DL/blob/fall18/_under_construction/homework01/homework_main.ipynb)
* [Тесты (придется установить Torch)](https://github.com/yandexdataschool/Practical_DL/blob/fall18/_under_construction/homework01/homework_test_modules.ipynb)

2) Применить ваш фреймворк для задачи классификации циферок, датасет [MNIST](http://yann.lecun.com/exdb/mnist/), построить график изменения loss(а лучше еще дополнительно и accuracy) в зависимости от эпохи. (вытяните каждую картинку в вектор, а каждую меточку y сделайте one hot вектором).

[**Код** ](Task3/)

[**Весь код в одном ноутбуке** ](task3_AIO_with_notes.ipynb)


## Задание 4

Ссылка на датасет: https://snap.stanford.edu/data/loc-gowalla.html

Задача:
1. Кластеризуем граф связей по аффинити пропагэйшин
2. Делаем чекины на трейн/тест
3. В рамках трейна считает топ по каждому кластеру
4. Строим рекомендации для теста - каждому топ его кластера
5. Оцениваем по precision@10 (точность по 10 рекомендациям)
6. Сравниваем с вариантом когда всем рекомендуется топ по тресну

[**Код** ](Task4.ipynb)
