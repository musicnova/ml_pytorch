3. Условное распределение
Пусть две случайные величины xi и eta принимают конечный набор значений: a1, ..., an и b1, ..., bm.
Пусть вероятности реализации каждой комбинации записаны в виде следующей таблицы
(которая представлена в виде матрицы).

Напишите python-функцию, которая вычисляет условное распределение случайной величины theta при условии того, что nu = b_0. На выходе должен быть одномерный python массив, в котором указаны вероятности p(theta = a_i | theta = b_0).

В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

import numpy as np

def conditional_a(P, a, b):
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


import numpy as np

def conditional_a(P, a, b):
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

https://ru.wikipedia.org/wiki/Условное_распределение
Тогда функция
ro_X|Y(x|y_0)=P(X=x|Y=y_0)=ro_X,Y(x,y_0)/ro_Y(y_0), foreach x in R^m
где ro_Y - функция вероятности случайной величины Y, называется усло́вной фу́нкцией вероя́тности случайной величины X при условии, что Y=y_0. Распределение, задаваемое условной функцией вероятности, называется условным распределением.
	
https://habr.com/ru/post/415373/
