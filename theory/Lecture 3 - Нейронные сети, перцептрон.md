

Перцептрон - простейший случай искусственной нейронной сети 

Искусственный нейрон. 
У искусственного нейрона есть произвольное количество входов и всегда один выход.

Функции активации:
- пороговая ( взвешенная сумма меньше 0 => 0, больше 0 => 1)
- сигмоидальная (как в логистической регрессии)
- ReLU (rectified linear unit) - меньше 0 => 0, больше 0 => само значение
- Leaky ReLU
- ...



Главная черта нейронных сетей - нейроны могут соединяться друг с другом (на входе нейрона выход другого)

Всегда есть 
- Входной слой (input layer)
- Скрытый слой (hidden layer) - их несколько
- Выходной слой (output layer)

Схема соединения нейронов - архитектура нейронной сети 

Перцептрон - первая архитектура нейронных сетей.
Нейроны организованы по слоям, при этом все значения из предыдущих слоев подаются на вход следующему слою. При этом других связей нет.
Полно связная нейронная сеть прямого распространения

![[Pasted image 20250325145513.png]]


У каждого нейрона есть свой вес


Скрытый слой преобразует исходные данные в признаки (внутренние, неинтерпретируемые) 
А выходной слой преобразует это оптимальные признаки в результат 

У каждого нейрона с картинки будет по 4 параметра (включая bias - смещение, равный 1), следовательно будет 16 параметров всего
В то время как у обычный логистической регрессии с тремя входными переменными будет всего 4 параметра 

Перцептрон устроен таким образом, что прохождение сигнала от входного слоя до выходного - это всего лишь перемножение матриц

Перемножение матриц очень хорошо параллелится и может вычисляться на GPU или TPU

Ключевой параметр нейронной сети - количество скрытых слоев

У современных нейронных сетей миллиарды и триллионы внутренних параметров

Вид зависимости признаков и целевой переменной может быть каким угодно 

Нейронные сети работают по принципу черного ящика. Невозможно объяснить, почему нейросеть обучилась именно так и выдает именно такие результаты.
А в некоторых предметных областях это может быть критически важно.
(
Кредитный скоринг - по законодательству ЕС необходимо объяснить причину отказа,
Медицинская диагностика
и.т.д.
)



Если в нейронной сети более одного скрытого слоя, то она называется **глубокой**



# Функции активации

## Выходные слои
### Сигмоидная
Используется при классификации в выходном слое
В скрытых слоях почти не используется, потому что за пределами интервала (-3, 3) стремится к асимптотам

### Гиперболический тангенс
Используется в выходных слоях при моделировании регрессии
Обладает те ми же недостатками, что и сигмоида

## Скрытые слои

### Soft Plus


### ReLU
$$h(u) = max[o, u]$$
Недостаток - отсутствие градиента в 0

### Leaky ReLU
$$h(u) = max[\alpha u, u]$$

## Функции потерь
стремимся их минимизировать

### MSE - среднеквадратичная ошибка

### logloss
