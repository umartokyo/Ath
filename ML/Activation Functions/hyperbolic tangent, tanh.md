2024/08/03, #ML #wiki #umarik 

Hyperbolic Tangent function is a type of [[activation function]] that maps inputs to the range between $-1$ and $1$. It is often used in hidden layers of a neural network because it centers the data, making the optimization process easier. It is defined as:

$$tanh(x)=\frac{e^x-e^{-x}}{e^x+e^{-x}}$$

![[tanh_curve.png]]
## Characteristics
- Similar to logistic, sigmoid but zero-centered.
- Prone to vanishing gradient problem.
## Use cases
- Hidden layers in some networks.
- Regression Problems.