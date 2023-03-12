

1. �������� �������������
����� ��� ��������� �������� xi � eta ��������� �������� ����� ��������: a1, ..., an � b1, ..., bm.
����� ����������� ���������� ������ ���������� �������� � ���� ��������� �������
(������� ������������ � ���� �������).

�������� python-���������, ������� ���������, ��� ��������� �������� ����������
(������ True, ���� �������� ����������, � False, ���� ��������).


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

� �������� ������ ���������� ��������� �������, �������� �� �� ����:

import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta

    res = ## YOUR CODE HERE

    return res


����������

� �������� ������� ������ ������� ������������ 4 �������.
������� ��������� � ���� ���������� ����� � ��������� utf-8.


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
z-����������: -1.6467438180091214
p-��������:   [0.04980536]

import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    res = (a.mean() - b.mean()) >= (1.0 - P).mean()

    return res

check_independence(np.matrix([[1,1],[1,1]]), np.array([1,2]), np.array([1,2]))

������������ ����� �� ����� #0



https://github.com/scikit-learn/scikit-learn/blob/main/sklearn/feature_selection/tests/test_mutual_info.py

����: P -- "matrix with probabilities, axis 0 -- xi, axis 1 -- eta".
����: a -- "array with outcomes for xi".
����: b -- "array with outcomes for eta".

����� ��� ��������� �������� xi � eta ��������� �������� ����� ��������: a1, ..., an � b1, ..., bm.
����� ����������� ���������� ������ ���������� �������� � ���� ��������� �������
(������� ������������ � ���� �������).

�������� python-���������, ������� ���������, ��� ��������� �������� ����������
(������ True, ���� �������� ����������, � False, ���� ��������).

� �������� ������ ���������� ��������� �������, �������� �� �� ����. ����������� ���� ���������������� python, ���������� numpy � ����� numpy.corrcoef. ������ �����, ������� �������. ��� ������ �� ���� � ����� �� python c ����������� numpy, ������ ��������� ����� � �����.

������:
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

�������:
import numpy as np

def check_independence(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    
    # �������� ��� ������� ��� �������� �������� ��������� ������� xi � eta
    xi = np.zeros(P.shape[0] * P.shape[1], dtype=np.int)
    eta = np.zeros(P.shape[0] * P.shape[1], dtype=np.int)
    
    # �������� ������� ���������� ��������� �������
    k = 0
    for i in range(P.shape[0]):
        for j in range(P.shape[1]):
            xi[k] = a[i]
            eta[k] = b[j]
            k += 1
    
    # �������� ������������� ��������� �������
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

������ �� ���� � ����� �� python c ����������� numpy:
https://www.geeksforgeeks.org/python-programming-language/
	
	
������������ ����� �� ����� #4


������ ��� ���� ���� � ������� check_independence � ������� ���������� a, b � P. ���� ����� ������, �� ����� ������� �� ������, ������ ������ �� ���� � ������ �������� ����.

ChatGPT, [11.03.2023 22:24]
def test_check_independence_2():
    a = 3
    b = 4
    P = 0.2
    assert check_independence(a, b, P) == False

������ �� ����: https://stackoverflow.com/questions/46851518/python-how-to-check-if-two-variables-are-independent

������ �������� ����: 
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
	
�����: