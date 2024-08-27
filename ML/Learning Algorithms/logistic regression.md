2024/08/22, #ML, #wiki #umarik 

Logistic regression is a binary [[classification]] algorithm. Note its usage of [[logistic, sigmoid]] activation function.

model:
$$z=\vec{w}*\vec{x}+b$$
activation function:
$$a_1=g(z)=\frac{1}{1+e^{-z}}=P(y=1\mid\vec{x}$$
$$a_2=1-a_1$$
loss function:
$$loss=-y\;log(a_1)-(1-y)\;log(1-a_1)$$
average loss:
$$J(\vec{w},b)$$