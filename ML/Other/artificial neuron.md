2024/08/02, #ML #wiki #umarik 

A neuron, also known as a node or unit, is the fundamental building block of [[neural network]]s. Inspired by biological neurons in the brain, artificial neurons in ML are designed to receive, process, and transmit information. However, remember that artificial neurons are over-simplified models of the neural neurons.
## Structure
An artificial neuron consists of several key components:
- **Inputs**: The neuron receives one or more input signals $(x₁, x₂, ..., xₙ)$.
- **Weights**: Each input is associated with a weight $(w₁, w₂, ..., wₙ)$, which represents the strength of the connection.
- **Bias**: An additional parameter ($b$) that allows the neuron to shift its activation function.
- **Summation Function**: Computes the weighted sum of inputs plus the bias.
- **Activation Function**: Determines the output of the neuron based on the summation result.
## Mathematical Representation
The output of a neuron can be represented mathematically as:
$$y=f(\sum(w_ix_i)+b)$$
where
- $y$ is the output
- $f(x)$ is the activation function
- $w_i$ are the weights
- $x_i$ are the inputs
- $b$ is the bias