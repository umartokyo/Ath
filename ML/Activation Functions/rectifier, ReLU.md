2024/07/31, #ML #wiki #umarik

Rectifier Linear Unit, aka ReLU is a type of [[activation function]], which returns positive part of the argument given. It denotes with an equation:

$$f(x)=x^+=\max(0,x)=\frac{x+|x|}{2}=\begin{cases} x & \text{if } x>0, \\ 0 & \text{otherwise},\end{cases}$$

![ReLU](relu_function.png)
## Characteristics:
- Simple and computationally efficient.
- Helps mitigate the [[vanishing gradient]] problem.
- Can suffer from dying ReLU problem. (neurons that always output 0)
## Use cases
- Default choice for many neural networks, especially in hidden layers.
- [[convolutional neural network, CNN]]