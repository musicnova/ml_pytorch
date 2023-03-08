
5. Argmin MAE

Пусть имеется набор данных x = [x_1,x_2,...,x_n], заданный в виде numpy массива. Чему будет равен argmin_mu(sum_i_1_n(abs(x_i-mu)))?

В качестве ответа реализуйте требуемую функцию, вызывать ее не надо:

import numpy as np

def argmin_mae(x):
    res = np.argmin(np.sum(np.absolute((y-x))))
    return res


Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде текстового файла в кодировке utf-8.


import numpy as np

def argmin_mae(x):
    res = np.argmin(np.sum(np.absolute((np.array([0.9539342, 0.84090066, 0.46451256, 0.09715253])-x))))
    return res


Ошибка на тесте #0
Детали: Traceback (most recent call last):
  File "solution.py", line 24, in <module>
    main()
  File "solution.py", line 21, in main
    result = argmin_mae(x)
  File "solution.py", line 7, in argmin_mae
    res = np.argmin(np.sum(np.absolute((np.array([0.9539342, 0.84090066, 0.46451256, 0.09715253])-x))))
ValueError: operands could not be broadcast together with shapes (4,) (19,)
	
	
https://stackoverflow.com/a/33359549

mae = np.sum(np.absolute((imageB.astype("float") - imageA.astype("float")))

https://stackoverflow.com/a/54964250

# Input data
dicts = {0: [0, 0, 0, 0], 1: [1, 0, 0, 0], 2: [1, 1, 0, 0], 3: [1, 1, 1, 0],4: [1, 1, 1, 1]}
new_value = np.array([0.9539342, 0.84090066, 0.46451256, 0.09715253])

# Convert values to array
values = np.array(list(dicts.values()))

# Compute the RMSE and get the index for the least RMSE 
rmse = np.mean((values-new_value)**2, axis=1)**0.5
index = np.argmin(rmse)    

print ("The closest value is %s" %(values[index]))
# The closest value is [1 1 0 0]

