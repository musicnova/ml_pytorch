

1. Проверка независимости
Пусть две случайные величины xi и eta принимают конечный набор значений: a1, ..., an и b1, ..., bm.
Пусть вероятности реализации каждой комбинации записаны в виде следующей таблицы
(которая представлена в виде матрицы).

Запишите python-выражение, которое проверяет, что случайные величины независимы
(выдает True, если величины независимы, и False, если зависимы).


=========================================
     |  b_0  |  b_1  |  ...  |  b_m-1   |
=========================================
 a_0 | p_0_0 | p_0_1 |  ...  |  p_0_m-1 |
=========================================
 a_1 | p_0_0 | p_0_0 |  ...  |  p_1_m-1 |
=========================================
 ... |  ...  |  ...  |  ...  |    ...   |
=========================================
a_n-1| p_0_0 | p_0_0 |  ...  | p_n-1_m-1|
=========================================

В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta

    res = ## YOUR CODE HERE

    return res


Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде текстового файла в кодировке utf-8.


import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta

    res = ## YOUR CODE HERE

    return res

https://habr.com/ru/post/556852/

a n:          284
b n:          16
z-статистика: -1.6467438180091214
p-значение:   [0.04980536]

import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    res = (a.mean() - b.mean()) >= (1.0 - P).mean()

    return res

check_independence(np.matrix([[1,1],[1,1]]), np.array([1,2]), np.array([1,2]))

Неправильный ответ на тесте #0



https://github.com/scikit-learn/scikit-learn/blob/main/sklearn/feature_selection/tests/test_mutual_info.py

Дано: P -- "matrix with probabilities, axis 0 -- xi, axis 1 -- eta".
Дано: a -- "array with outcomes for xi".
Дано: b -- "array with outcomes for eta".

Здесь две случайные величины xi и eta принимают конечный набор значений: a1, ..., an и b1, ..., bm.
Пусть вероятности реализации каждой комбинации записаны в виде следующей таблицы
(которая представлена в виде матрицы).

Запишите python-выражение, которое проверяет, что случайные величины независимы
(выдает True, если величины независимы, и False, если зависимы).

В качестве ответа реализуйте требуемую функцию, вызывать ее не надо. Используйте язык программирования python, библиотеку numpy и метод numpy.corrcoef. Напиши тесты, объясни решение. Дай ссылку на сайт с кодом на python c библиотекой numpy, указав несколько строк с кодом.

Пример:
import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta

    res = ## YOUR CODE HERE

    return res

ChatGPT, [11.03.2023 22:18]
# Test
P = np.array([[0.25, 0.25, 0.25, 0.25],
              [0.25, 0.25, 0.25, 0.25],
              [0.25, 0.25, 0.25, 0.25],
              [0.25, 0.25, 0.25, 0.25]])
a = np.array([1, 2, 3, 4])
b = np.array([1, 2, 3, 4])

print(check_independence(P, a, b)) # True

Решение:
import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    
    # Создадим два массива для хранения значений случайных величин xi и eta
    xi = np.zeros(P.shape[0] * P.shape[1], dtype=np.int)
    eta = np.zeros(P.shape[0] * P.shape[1], dtype=np.int)
    
    # Заполним массивы значениями случайных величин
    k = 0
    for i in range(P.shape[0]):
        for j in range(P.shape[1]):
            xi[k] = a[i]
            eta[k] = b[j]
            k += 1
    
    # Проверим независимость случайных величин
    res = np.abs(np.corrcoef(xi, eta)[0, 1]) < 0.001
    
    return res

# Test
P = np.array([[0.25, 0.25, 0.25, 0.25],
              [0.25, 0.25, 0.25, 0.25],
              [0.25, 0.25, 0.25, 0.25],
              [0.25, 0.25, 0.25, 0.25]])
a = np.array([1, 2, 3, 4])
b = np.array([1, 2, 3, 4])

print(check_independence(P, a, b)) # True

Ссылка на сайт с кодом на python c библиотекой numpy:
https://www.geeksforgeeks.org/python-programming-language/
	
	
Неправильный ответ на тесте #4


допиши ещё один тест к функции check_independence с другими значениями a, b и P. Если будет ошибка, то поищи решение на сайтах, напиши ссылку на сайт и цитату похожего кода.

ChatGPT, [11.03.2023 22:24]
def test_check_independence_2():
    a = 3
    b = 4
    P = 0.2
    assert check_independence(a, b, P) == False

Ссылка на сайт: https://stackoverflow.com/questions/46851518/python-how-to-check-if-two-variables-are-independent

Цитата похожего кода: 
"if(probability_of_A_given_B == probability_of_A):
    print("A and B are independent")
else:
    print("A and B are dependent")"

2

https://datascience.stackexchange.com/questions/35787/testing-independence-of-random-variables-in-python
This is a hard problem to solve and there are many tests that attempt to answer it.. One way of testing it is using mutual information, available on scikit-learn for either continuous variables or discrete variables. It returns zero for independent variables and higher values the more dependence there is between the variables (makes it harder to call something "independent/dependent" but makes it easier to rank features by their independence).

from sklearn.feature_selection import mutual_info_regression
import numpy as np

x = np.linspace(0, 10, 50)
y = x + np.random.randn(50)
z = np.random.randn(50)

# reshape necessary because the function accepts many
# features at once to be compared with the right-hand side
print(mutual_info_regression(x.reshape(-1, 1), y))
print(mutual_info_regression(x.reshape(-1, 1), z))

> 1.20832658
> 0
	
Итого: