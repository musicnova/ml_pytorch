2. Производная бинарной кросс-энтропии

Чему равна !!! производная !!! бинарной кросс-энтропии? 

d/dx[-t*log(sigma(a*x + b) - (1 - t) * log(1 - sigma(a * x + b))]

theta(x) = 1. / (1. + np.exp(-x))

В качестве ответа реализуйте требуемую функцию.
Функция должна вычислять значение производной в заданной точке.
В ответе сигмоиду представить в !!! экспоненциальном !!! виде.

Вызывать функцию не надо:
import numpy as np

def bce_grad(x, t, a, b):
    res = ## YOUR CODE HERE
    return res


Примечание

В качестве отступа внутри функции используется 4 пробела.
Решение отправить в виде !!! текстового файла !!! в кодировке utf-8.

https://www.wolframalpha.com/input?i=d%2Fdx%5B-t*log%28%281+%2F+%281+%2B+exp%28a*x+%2B+b%29%29%29+-+%281+-+t%29+*+%281+%2F+%281+%2B+log%281+-+exp%28a+*+x+%2B+b%29%29%29%29%5D

import numpy as np

def bce_grad(x, t, a, b):
    res = -1.0 * (t * (-a * (1 - t) * np.exp(a * x + b) / ((1 - np.exp(a * x + b)) * (np.log(1 - np.exp(a * x + b)) + 1) * (np.log(1 - np.exp(a * x + b)) + 1)) - (a * np.exp(a * x + b)) / ((np.exp(a * x + b) + 1)*(np.exp(a * x + b) + 1))) / (1/(np.exp(a * x + b) + 1) - (1 - t)/(np.log(1 - np.exp(a * x + b)) + 1)))
    return res


Неправильный ответ на тесте #0
	
https://gist.github.com/martinferianc/38c57e7089b985f26c34e1b2bd353dd9

    # Define the binary cross-entropy function derivative
    def dbce(self, yhat, y):
        return -(y / (yhat+1e-8) - (1 - y) / (1 - yhat+1e-8))


		
	
Derivative

d/dx(-t log(1/(1 + exp(a x + b)) - (1 - t)/(1 + log(1 - exp(a x + b))))) = -(t (-(a (1 - t) e^(a x + b))/((1 - e^(a x + b)) (log(1 - e^(a x + b)) + 1)^2) - (a e^(a x + b))/(e^(a x + b) + 1)^2))/(1/(e^(a x + b) + 1) - (1 - t)/(log(1 - e^(a x + b)) + 1))
	
	
	
WOLFRAM https://www.wolframalpha.com/input?i=d%2Fdx%5B-t*log%281e-7*%28a*x+%2B+b%29+-+%281+-+t%29+*+log%281+-+1e-7*%28a+*+x+%2B+b%29%29%5D
d/dx(-t log(1×10^(-7) (a x + b) - (1 - t) log(1 - 1×10^(-7) (a x + b)))) = -(a t (a x + b + 10000000 t - 20000000))/((a x + b - 10000000) (10000000 (t - 1) log((-a x - b)/10000000 + 1) + a x + b))
	
https://towardsdatascience.com/nothing-but-numpy-understanding-creating-binary-classification-neural-networks-with-e746423c8d5c
For the next calculation, we’ll need the derivative of the Sigmoid function which forms the local gradient at the red node. The derivative if the Sigmoid function is(derived in detail in my previous post):

p_hat = sigma(z) = 1 / (1 + exp(-z))
	
	
https://stackoverflow.com/a/67616451

def BinaryCrossEntropy(y_true, y_pred):
    y_pred = np.clip(y_pred, 1e-7, 1 - 1e-7)
    term_0 = (1-y_true) * np.log(1-y_pred + 1e-7)
    term_1 = y_true * np.log(y_pred + 1e-7)
    return -np.mean(term_0+term_1, axis=0)

print(BinaryCrossEntropy(np.array([1, 1, 1]).reshape(-1, 1), 
                         np.array([1, 1, 0]).reshape(-1, 1)))


import numpy as np

def bce_grad(x, t, a, b):
    res = -1.0 * (a *  θ t (a θ x + b θ + t - 2))/((a θ x + b θ - 1) ((t - 1) log(1 - θ (a x + b)) + θ (a x + b)))
    return res
	
	

	
	
https://towardsdatascience.com/understanding-binary-cross-entropy-log-loss-a-visual-explanation-a3ac6025181a

Loss Function: Binary Cross-Entropy / Log Loss

If you look this loss function up, this is what you’ll find:
	
Рис. 58. Конечная стабильная и упрощенная бинарная кросс-энтропийная функция

Давайте подтвердим, что он правильно вычисляет отрицательные и положительные значения:



https://gist.github.com/liampearson/7aee8087c2fe4ab79fff67d226636e0c

https://gist.github.com/bkj/2c4ae03439935e52ad3dca6478a005d4

    x  = torch.randn((100, 10)) * scale
    sx = torch.sigmoid(x)
    y  = (torch.rand((100, 10)) < 0.1).float()
    
    i, j = np.where(y.numpy())
    i, j = torch.LongTensor(i), torch.LongTensor(j)
    
    bce_logits         = loss(x, y)
    bce_sigmoid        = sloss(sx, y)
    bce_sigmoid_manual = - (y * sx.log() + (1 - y) * (1 - sx).log()).mean()
    bce_logit_manual   = (x.clamp(min=0) - x * y + torch.log(1 + torch.exp(-torch.abs(x)))).mean()
    bce_logit_sparse   = sparse_bce_with_logits(x, i, j)
    