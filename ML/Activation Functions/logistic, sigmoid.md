2024/08/03, #ML #wiki #umarik 

Logistic function, aka sigmoid is a type of [[activation function]] mainly used for [[binary classification]] and [[logistic regression]] algorithms. It compresses the value into the range between zero and one following the equation:

$$\sigma(x)=\frac{1}{1+e^{-x}}$$

![[logistic_curve.png]]
## Characteristics
- S-shaped curve
- Historically popular, but less used in hidden layers now.
- Prone to [[vanishing gradient]] problem for very high or low values.
## Use cases:
- [[binary classification]]. (output layer)
- Gates in certain [[recurrent neural network]] architectures.