

2. ������� �������������
����� ��� ��������� �������� xi � eta ��������� �������� ����� ��������: a1, ..., an � b1, ..., bm.
����� ����������� ���������� ������ ���������� �������� � ���� ��������� �������
(������� ������������ � ���� �������).

�������� python �������, ������� ��������� ������� ������������� ��������� �������� theta.
�� ������ ������ ���� ���������� python ������, � ������� ������� ����������� p(theta = a_i).

� �������� ������ ���������� ��������� �������, �������� �� �� ����:

import numpy as np

def marginal_a(P, a, b):
    # P -- matrix with probabilities, axis 0 -- xi, axis 1 -- eta
    # a -- array with outcomes for xi
    # b -- array with outcomes for eta
    # P.shape[0] == b.shape[0]
    # P.shape[1] == a.shape[0]

    res = ## YOUR CODE HERE

    return res


����������

� �������� ������� ������ ������� ������������ 4 �������.
������� ��������� � ���� ���������� ����� � ��������� utf-8.

# Function to calculate Mutual Information 
def mutual_information(x, y, bins): 
    c_xy = np.histogram2d(x, y, bins)[0] 
    mi = mutual_info_score(None, None, contingency=c_xy) 
    return mi 

import numpy as np

def marginal_a(P, a, b):
    """
    ������� ��� �������� ������������ ����������� ���������� a ��� ������������� �������� ���������� b.

    ���������:
    P -- ������� ������������ ����������� ������������� ���� ����������;
    a -- ���������� ��� ������� ������ ������������ �����������;
    b -- ����������, ��� ������� ����������� ��������.

    ����������:
    ������������ ����������� ���������� a ��� ������������� �������� ���������� b.
    """

    # �������������� ����� ������������
    marginal_a = 0

    # �������� �� ���� ������� ������� ������������
    for row in range(len(P)):
        # ���������, ������������� �� ������� �������� ���������� b ���������
        if b == row:
            # ��������� ����������� � �����
            marginal_a += P[row][a]

    # ���������� ������������ �����������
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

������������ ����� �� ����� #0

https://ru.wikipedia.org/wiki/�������_�������������#:~:text=�������%20�������������%20(������������%20�������������)%20�,���������%20����������%20����������%20������������%20�������������.

������� ������������� (������������ �������������) � ������������� ������������� ����� ��� ��������� ��������� �������, ��������������� � �������� ���������� ��� ��������� ��������� ���������� ���������� ������������ �������������.



������ ����������� � ���� �� https://github.com/scikit-learn/scikit-learn/blob/main/sklearn/feature_selection/tests/test_mutual_info.py


�������, ��� ��������� ������������� ���� ��������� �������?


����� ��� ��������� �������� xi � eta ��������� �������� ����� ��������: a1, ..., an � b1, ..., bm.

����� �������� �� ����� python ������� marginal_a(P, a, b) � ����������� numpy, �� ������ ������� ������ ���� ���������� python ������, � ������� ������� ����������� p(theta = a_i).
������ �����, ������� �������. ��� ������ �� ���� � ����� �� python c ����������� numpy, ������ ��������� ����� � �����.

������:
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

# �������
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

# ������ �� ���� � ����� �� python c ����������� numpy:
# https://www.w3schools.com/python/numpy_intro.asp

Yo Basov, [11.03.2023 23:00]
������ ��� ���� ���� � ������� check_independence � ������� ���������� a, b � P. ���� ����� ������, �� ����� ������� �� ������, ������ ������ �� ���� � ������ �������� ����.

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

��� �������� ������������� ���� ��������� ������� ����� ������������ �������� ������� � ����������� ���������� �������. ���� ����������� �������� ������� ����������� ����� ����� ���������� ����������. �� ����� ����, ���� ��� ��������� �������� ����������.

�� ����� https://www.geeksforgeeks.org/python-calculate-mutual-information-between-two-random-variables/ ����� ����� ������ ���� �� python � ����������� numpy, ������� ��������� ��������� ������������� ���� ��������� �������.

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
������ ��� ���� ���� � ������� check_independence � ������� ���������� a, b � P. ���� ����� ������, �� ����� ������� �� ������, ������ ������ �� ���� � ������ �������� ����.

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

��� �������� ������������� ���� ��������� ������� ����� ������������ �������� ������� � ����������� ���������� �������. ���� ����������� �������� ������� ����������� ����� ����� ���������� ����������. �� ����� ����, ���� ��� ��������� �������� ����������.

�� ����� https://www.geeksforgeeks.org/python-calculate-mutual-information-between-two-random-variables/ ����� ����� ������ ���� �� python � ����������� numpy, ������� ��������� ��������� ������������� ���� ��������� �������.

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

# ������� �� ����� stackoverflow.com:
https://stackoverflow.com/questions/482036/how-do-i-check-if-a-number-is-between-two-numbers

������:
def is_between(x, y, z):
    return y <= x <= z

ChatGPT, [11.03.2023 23:03]
def marginal_a(P, a, b):
    """
    ������� ��� �������� ������������ ����������� ���������� a ��� ������������� �������� ���������� b.

    ���������:
    P -- ������� ������������ ����������� ������������� ���� ����������;
    a -- ���������� ��� ������� ������ ������������ �����������;
    b -- ����������, ��� ������� ����������� ��������.

    ����������:
    ������������ ����������� ���������� a ��� ������������� �������� ���������� b.
    """

    # �������������� ����� ������������
    marginal_a = 0

    # �������� �� ���� ������� ������� ������������
    for row in range(len(P)):
        # ���������, ������������� �� ������� �������� ���������� b ���������
        if b == row:
            # ��������� ����������� � �����
            marginal_a += P[row][a]

    # ���������� ������������ �����������
    return marginal_a