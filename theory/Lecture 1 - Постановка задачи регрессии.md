
набор данных, используемый для обучения модели - DataSet (X)

целевая переменная (y) - зависимая переменная,
остальные атрибуты X - независимые переменные, признаки, факторы

вектор целевой переменной не входит в матрицу атрибутов

Регрессионная модель - функция, которая принимает на вход значения атрибутов какого-то конкретного объекта и выдает предполагаемое значение целевой переменной

ОБЫЧНО мы предполагаем, что целевая переменная одна

РЕГРЕССИЮ ПОДРАЗДЕЛЯЕТ НА
- Парную - всего 1 атрибут
- Множественную - больше 1го


В задаче регрессии в качестве ФУНКЦИИ ОШИБКИ чаще всего берут среднее квадратичное отклонение / 2 * кол-во измерений 

mean square error (MSE) - L2-ошибка - средний квадрат отклонений теоретических значений от эмпирических

![[Pasted image 20250227195516.png]]

в качестве АРГУМЕНТОВ функции ошибки выступают ПАРАМЕТРЫ ФУНКЦИИ ГИПОТЕЗЫ


Функция ошибки нужна чтобы отличать хорошие модели от плохих



# МЕТОД ГРАДИЕНТНОГО СПУСКА

в плейлисте есть реализация градиентного спуска

реализация сводится к подбору значений alpha и кол-ва итераций, а также их прерывания


модель на графике рисуется только следующим образом

```py
x_pred = np.linspace(from, to, points_count)
y_pred = model.predict(x_pred)
plt.plot(x_pred, y_pred, 'r')

```
рисует линию на графике 




# РЕГРЕССИЯ C НЕСКОЛЬКИМИ ПЕРЕМЕННЫМИ

В любой модели линейной регрессии количество количество параметров на единицу больше количества входных переменных 
b0 + b1 * x - 2 параметра и 1 входная переменная 



разложение функции в ряд Тейлора 

полиномиальным рядом можно аппроксимировать в принципе любую функцию
при достаточно больших степенях можно аппроксимировать любое расположение точек

для этого обычно берут все комбинации факторов до какой-то степени полинома
![[Pasted image 20250228170626.png]]

```py


lr = LinearRegression()

california = fetch_california_housing()

X, y = california.data, california.target

lr.fit(X, y)

lr.coef_  # - b_1, b_2, ... , b_i
lr.intercept_  # - b_0

lr.score() # - r2 metrics
```
