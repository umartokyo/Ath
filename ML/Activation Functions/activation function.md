2024/08/03, #ML #wiki #umarik 

Activation functions are used in [[neural network]]s to determine the output of a [[neuron]] based on its input. They introduce non-linearity into the network allowing it to learn more complex patters. They enable [[backpropagation]], meaning they are differentiable, allowing for gradient-based optimization. Activation functions also introduce non-linearity and [normalize](normalization.md) outputs, keeping the neuron's output within a specific range for ease of training.
## Activation Functions
1. [[logistic, sigmoid]]
2. [[hyperbolic tangent, tanh]]
3. [[rectifier, ReLU]]
4. [[leaky ReLU]]
5. [[softmax]]
## Choosing Activation Functions
Factors to consider:
1. Type of problem
2. Network architecture
3. Desired properties
4. Computational efficiency

General guidelines:
- Hidden layers: [[rectifier, ReLU]] or its variants are often a good default choice.
- Output layer: Depends of a problem, usually [[logistic, sigmoid]] for binary classification and [[softmax]] for multi-class.
### Impact on Learning
- Affects the speed of training convergence.
- Influences the occurrence of problems like [[vanishing gradient]] or [[exploding gradient]].
- Can impact the network's ability to approximate complex functions.


