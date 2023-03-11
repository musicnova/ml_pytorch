На языке python посчитай выражение для одной итерации градиентного спуска со скоростью alpha для минимизации функции f(x,y) = 0.5*(y-(a*x+b))*(y-(a*x+b)).

Пример:
import numpy as np

def bce_grad(x, y, a, b, alpha):
    a = ## YOUR CODE HERE
    b = ## YOUR CODE HERE

    res = np.array([a, b])
    return res

ChatGPT, [11.03.2023 18:33]
# Пример вызова:
bce_grad(x, y, a, b, alpha)

# Ответ:
import numpy as np

def bce_grad(x, y, a, b, alpha):
    a = a - alpha * (y - (a * x + b)) * x
    b = b - alpha * (y - (a * x + b))

    res = np.array([a, b])
    return res

	
4. Градиентный спуск
Запишите выражение для одной итерации градиентного спуска для минимизации функции

0.5*(y-(a*x+b))*(y-(a*x+b)), speed = alpha, grad = ?

В этой задаче alpha положительная.
В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

import numpy as np

def bce_grad(x, y, a, b, alpha):
    a = -alpha * np.sum(a, axis = 0, keepdims = True) / np.array([x, y]).shape[1]
    b = -alpha * np.sum(b, axis = 0, keepdims = True) / np.array([x, y]).shape[1]

    res = np.array([a, b])
    return res

Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде текстового файла в кодировке utf-8.

!!!
Ошибка на тесте #0
Детали: Traceback (most recent call last):
  File "solution.py", line 25, in <module>
    main()
  File "solution.py", line 22, in main
    result = bce_grad(x, y, a, b, alpha)
  File "solution.py", line 6, in bce_grad
    a = -alpha * np.sum(a, axis = 0, keepdims = True) / np.array([x, y]).shape[1]
IndexError: tuple index out of range
!!!

https://www.wolframalpha.com/input?i=d%2Fdx%5B-t*log%28%281+%2F+%281+%2B+exp%28a*x+%2B+b%29%29%29+-+%281+-+t%29+*+%281+%2F+%281+%2B+log%281+-+exp%28a+*+x+%2B+b%29%29%29%29%5D

https://habr.com/ru/post/318970/
Зачем нужны ухищрения

Напомню, как выглядят формулы для обычного градиентного спуска:
\Delta \theta = -\eta \nabla_\theta J( \theta)


\theta = \theta + \Delta \theta = \theta - \eta \nabla_\theta J( \theta)

где \inline \theta — параметры сети, \inline J( \theta) — целевая функция или функция потерь в случае машинного обучения, а \inline \eta — скорость обучения. 

https://habr.com/ru/post/467185/
И вот наш градиент — вектор из частных производных (обозначается символом $\nabla$ [набла], перевернутым треугольником, т.е. перевернутой [дельтой]):

https://gist.github.com/martinferianc/38c57e7089b985f26c34e1b2bd353dd9
        # Compute the gradient for the previous layer
        dA_curr = np.dot(dA_curr, W)
