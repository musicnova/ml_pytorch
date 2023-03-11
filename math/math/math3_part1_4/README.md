4. Дисперсия произведения
Пусть две случайные величины xi и eta принимают конечный набор значений: a1, ..., an и b1, ..., bm.
Пусть вероятности реализации каждой комбинации записаны в виде следующей таблицы
(которая представлена в виде матрицы).



В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

Напишите функцию, которая вычисляет дисперсию случайной величины theta(nu). На выходе должно быть float значение.

import numpy as np

def var_ab(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    # P.shape[0] == b.shape[0]
    # P.shape[1] == a.shape[0]

    var = ## YOUR CODE HERE

    return var


Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде текстового файла в кодировке utf-8.

import numpy as np

def var_ab(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    # P.shape[0] == b.shape[0]
    # P.shape[1] == a.shape[0]
    p = 1.0 / (1.0 + np.exp(-P.dot(b) - a))
    da = a - p
    var = np.var(np.array(da).flatten())

    return var

var_ab(np.matrix([[1,1],[1,1]]), np.array([1,2]), np.array([1,2]))


Неправильный ответ на тесте #0

https://runebook.dev/ru/docs/numpy/reference/generated/numpy.var

 numpy.var( a , axis=None , dtype=None , out=None , ddof=0 , keepdims=<нет значения> , * , где=<нет значения> ) [источник]

    Вычислите дисперсию вдоль указанной оси.

    Возвращает дисперсию элементов массива,меру распространения распределения.По умолчанию дисперсия вычисляется для сплющенного массива,в противном случае по указанной оси.