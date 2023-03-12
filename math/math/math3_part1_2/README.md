

2. Частное распределение
Пусть две случайные величины xi и eta принимают конечный набор значений: a1, ..., an и b1, ..., bm.
Пусть вероятности реализации каждой комбинации записаны в виде следующей таблицы
(которая представлена в виде матрицы).

Напишите python функцию, которая вычисляет частное распределение случайной величины theta.
На выходе должен быть одномерный python массив, в котором указаны вероятности p(theta = a_i).

В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

import numpy as np

def marginal_a(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    # P.shape[0] == b.shape[0]
    # P.shape[1] == a.shape[0]

    res = ## YOUR CODE HERE

    return res


Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде текстового файла в кодировке utf-8.

# Function to calculate Mutual Information 
def mutual_information(x, y, bins): 
    c_xy = np.histogram2d(x, y, bins)[0] 
    mi = mutual_info_score(None, None, contingency=c_xy) 
    return mi 

import numpy as np

def marginal_a(P, a, b):
    """
    Функция для подсчета маргинальной вероятности переменной a при фиксированном значении переменной b.

    Аргументы:
    P -- матрица вероятностей совместного распределения двух переменных;
    a -- переменная для которой ищется маргинальная вероятность;
    b -- переменная, для которой фиксируется значение.

    Возвращает:
    Маргинальная вероятность переменной a при фиксированном значении переменной b.
    """

    # инициализируем сумму вероятностей
    marginal_a = 0

    # проходим по всем строкам матрицы вероятностей
    for row in range(len(P)):
        # проверяем, соответствует ли текущее значение переменной b заданному
        if b == row:
            # добавляем вероятность в сумму
            marginal_a += P[row][a]

    # возвращаем маргинальную вероятность
    return marginal_a
	
def test_marginal_a():
    P = np.array([[0.2, 0.3, 0.5],
                  [0.4, 0.2, 0.4],
                  [0.4, 0.5, 0.1]])
    a = np.array([1, 2, 3])
    b = np.array([4, 5, 6])
    expected = np.array([0.2, 0.5, 0.3])
    
    # check result
    assert np.allclose(marginal_a(P, a, b), expected)

test_marginal_a()
	
import numpy as np

def marginal_a(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    # P.shape[0] == b.shape[0]
    # P.shape[1] == a.shape[0]
    p = 1.0 / (1.0 + np.exp(-P.dot(b) - a))
    da = a - p
    res = np.array(da).flatten()

    return res

marginal_a(np.matrix([[1,1],[1,1]]), np.array([1,2]), np.array([1,2]))

Неправильный ответ на тесте #0

https://ru.wikipedia.org/wiki/Частное_распределение#:~:text=Частное%20распределение%20(маргинальное%20распределение)%20—,компонент%20некоторого%20известного%20многомерного%20распределения.

Частное распределение (маргинальное распределение) — вероятностное распределение одной или множества случайных величин, рассматриваемых в качестве компоненты или множества компонент некоторого известного многомерного распределения.



Добавь комментарии к коду на https://github.com/scikit-learn/scikit-learn/blob/main/sklearn/feature_selection/tests/test_mutual_info.py


Объясни, как проверить независимость двух случайных величин?


Пусть две случайные величины xi и eta принимают конечный набор значений: a1, ..., an и b1, ..., bm.

Нужно написать на языке python функцию marginal_a(P, a, b) с библиотекой numpy, на выходе которой должен быть одномерный python массив, в котором указаны вероятности p(theta = a_i).
Напиши тесты, объясни решение. Дай ссылку на сайт с кодом на python c библиотекой numpy, указав несколько строк с кодом.

Пример:
import numpy as np

def marginal_a(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    # P.shape[0] == b.shape[0]
    # P.shape[1] == a.shape[0]

    res = ## YOUR CODE HERE

    return res

ChatGPT, [11.03.2023 22:58]
# Test 1
P = np.array([[0.2, 0.3, 0.5],
              [0.4, 0.1, 0.5]])
a = np.array([1, 2, 3])
b = np.array([4, 5])

assert np.allclose(marginal_a(P, a, b), np.array([0.6, 0.3, 0.1]))

# Test 2
P = np.array([[0.3, 0.4, 0.3],
              [0.1, 0.2, 0.7]])
a = np.array([2, 3, 4])
b = np.array([5, 6])

assert np.allclose(marginal_a(P, a, b), np.array([0.4, 0.4, 0.2]))

# Решение
import numpy as np

def marginal_a(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    # P.shape[0] == b.shape[0]
    # P.shape[1] == a.shape[0]

    res = np.sum(P, axis=0)

    return res

# Test 1
P = np.array([[0.2, 0.3, 0.5],
              [0.4, 0.1, 0.5]])
a = np.array([1, 2, 3])
b = np.array([4, 5])

assert np.allclose(marginal_a(P, a, b), np.array([0.6, 0.3, 0.1]))

# Test 2
P = np.array([[0.3, 0.4, 0.3],
              [0.1, 0.2, 0.7]])
a = np.array([2, 3, 4])
b = np.array([5, 6])

assert np.allclose(marginal_a(P, a, b), np.array([0.4, 0.4, 0.2]))

# Ссылка на сайт с кодом на python c библиотекой numpy:
# https://www.w3schools.com/python/numpy_intro.asp

Yo Basov, [11.03.2023 23:00]
допиши ещё один тест к функции check_independence с другими значениями a, b и P. Если будет ошибка, то поищи решение на сайтах, напиши ссылку на сайт и цитату похожего кода.

ChatGPT, [11.03.2023 23:00]
def test_marginal_a():
    P = np.array([[0.2, 0.3, 0.5],
                  [0.4, 0.2, 0.4],
                  [0.4, 0.5, 0.1]])
    a = np.array([1, 2, 3])
    b = np.array([4, 5, 6])
    expected = np.array([0.2, 0.5, 0.3])
    
    # check result
    assert np.allclose(marginal_a(P, a, b), expected)

test_marginal_a()

Для проверки независимости двух случайных величин можно использовать критерий Мэтьюса — коэффициент информации Мэтьюса. Этот коэффициент измеряет степень зависимости между двумя случайными величинами. Он равен нулю, если две случайные величины независимы.

На сайте https://www.geeksforgeeks.org/python-calculate-mutual-information-between-two-random-variables/ можно найти пример кода на python с библиотекой numpy, который позволяет проверить независимость двух случайных величин.

# Python3 program to calculate 
# Mutual Information between two random variables 
import numpy as np 
  
# Function to calculate Mutual Information 
def mutual_information(x, y, bins): 
    c_xy = np.histogram2d(x, y, bins)[0] 
    mi = mutual_info_score(None, None, contingency=c_xy) 
    return mi 
  
# Driver Code 
x = [1, 1, 1, 1, 1, 0, 0, 0, 0, 0] 
y = [0, 0, 1, 1, 0, 0, 0, 1, 1, 1] 
bins = 3
print(mutual_information(x, y, bins))

Yo Basov, [11.03.2023 23:00]
допиши ещё один тест к функции check_independence с другими значениями a, b и P. Если будет ошибка, то поищи решение на сайтах, напиши ссылку на сайт и цитату похожего кода.

ChatGPT, [11.03.2023 23:00]
def test_marginal_a():
    P = np.array([[0.2, 0.3, 0.5],
                  [0.4, 0.2, 0.4],
                  [0.4, 0.5, 0.1]])
    a = np.array([1, 2, 3])
    b = np.array([4, 5, 6])
    expected = np.array([0.2, 0.5, 0.3])
    
    # check result
    assert np.allclose(marginal_a(P, a, b), expected)

test_marginal_a()

Для проверки независимости двух случайных величин можно использовать критерий Мэтьюса — коэффициент информации Мэтьюса. Этот коэффициент измеряет степень зависимости между двумя случайными величинами. Он равен нулю, если две случайные величины независимы.

На сайте https://www.geeksforgeeks.org/python-calculate-mutual-information-between-two-random-variables/ можно найти пример кода на python с библиотекой numpy, который позволяет проверить независимость двух случайных величин.

# Python3 program to calculate 
# Mutual Information between two random variables 
import numpy as np 
  
# Function to calculate Mutual Information 
def mutual_information(x, y, bins): 
    c_xy = np.histogram2d(x, y, bins)[0] 
    mi = mutual_info_score(None, None, contingency=c_xy) 
    return mi 
  
# Driver Code 
x = [1, 1, 1, 1, 1, 0, 0, 0, 0, 0] 
y = [0, 0, 1, 1, 0, 0, 0, 1, 1, 1] 
bins = 3
print(mutual_information(x, y, bins))

ChatGPT, [11.03.2023 23:02]
def test_check_independence_2():
    assert check_independence(a=0.3, b=0.5, P=0.7) == False

# Решение на сайте stackoverflow.com:
https://stackoverflow.com/questions/482036/how-do-i-check-if-a-number-is-between-two-numbers

Цитата:
def is_between(x, y, z):
    return y <= x <= z

ChatGPT, [11.03.2023 23:03]
def marginal_a(P, a, b):
    """
    Функция для подсчета маргинальной вероятности переменной a при фиксированном значении переменной b.

    Аргументы:
    P -- матрица вероятностей совместного распределения двух переменных;
    a -- переменная для которой ищется маргинальная вероятность;
    b -- переменная, для которой фиксируется значение.

    Возвращает:
    Маргинальная вероятность переменной a при фиксированном значении переменной b.
    """

    # инициализируем сумму вероятностей
    marginal_a = 0

    # проходим по всем строкам матрицы вероятностей
    for row in range(len(P)):
        # проверяем, соответствует ли текущее значение переменной b заданному
        if b == row:
            # добавляем вероятность в сумму
            marginal_a += P[row][a]

    # возвращаем маргинальную вероятность
    return marginal_a