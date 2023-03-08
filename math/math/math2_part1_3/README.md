2. Ортогонализация

Напишите функцию, которая вычисляет компоненту вектора a, ортогональную вектору b.

В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

import numpy as np

def orthogonalization(a, b):
    res = ## YOUR CODE HERE
    return res


Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде текстового файла в кодировке utf-8.

import numpy as np

def orthogonalization(a, b):
    res = np.cross(a / np.linalg.norm(a), b  / np.linalg.norm(b))
    return res
	
orthogonalization([1, 1, 0], [1, 0, 0])


Неправильный ответ на тесте #0


https://stackoverflow.com/a/50548327

b1 = np.cross(u, [1, 0, 0])
b2 = np.cross(u, b1)
b1, b2 = b1 / np.linalg.norm(b1), b2 / np.linalg.norm(b2)

