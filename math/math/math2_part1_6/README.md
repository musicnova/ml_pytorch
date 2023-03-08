4. Сингулярные числа и сингулярные векторы

Пусть сингулярные числа матрицы A записаны в векторе _s в порядке убывания.
Количество координат в этом векторе не меньше двух.

Пусть имеются два ортогональных вектора единичной длины _x и _y.
Какое самое большое соотношение np.abs(A * x - A * y) / np.abs(x - y) возможно?

В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

import numpy as np

def relation(s):
    res = len(np.dot(np.ones((len(s),len(s))).reshape(len(s),len(s)), s))
    return res

relation(np.array([1,2,3]))

Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде текстового файла в кодировке utf-8.

import numpy as np

def relation(s):
    res = ## YOUR CODE HERE
    return res


Неправильный ответ на тесте #0

https://proproprogs.ru/modules/numpy-proizvedenie-matric-i-vektorov-elementy-lineynoy-algebry
Умножение вектора на матрицу
Наконец, рассмотрим умножение вектора на матрицу. Это также можно записать двумя способами:
a = np.array([1,2,3])
b = np.arange(4,10).reshape(3,2) # матрица 3x2
И, затем, воспользуемся уже знакомой нам функцией dot:

np.dot(a, b) # array([40, 46])