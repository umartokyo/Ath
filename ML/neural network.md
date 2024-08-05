2024/08/02, #ML #wiki #umarik 

Neural network is a computational model inspired by the way biological neural networks from our brains process information. It consists of layers of [[neuron]]s, which makes it possible for the model to learn and make decision based on the input data. Neural networks are key components for deep learning and are widely used for tasks like [[classification]], [[regression]], image and [[speech recognition]]...

![[neural_network.png]]
## Structure
Neural network consists of three main categories: 
- **Input Layer**: Receives the initial data. Each neuron represents a feature from your dataset.
- **Hidden Layer**(s): Processes the information from the previous layer.
	- **Shallow Neural Network** - a neural network with single hidden layer.
	- **Deep Neural Network** - a neural network with multiple hidden layers.
- **Output Layer**: Returns the final result / prediction.
## Key Components
1. [Neurons / Nodes](neuron): Basic units, that receive input, process it, and return output.
2. Weights: A certain value which indicated the strength of the connection between neurons.
3. Bias: An additional parameter to the adjust the output of each neuron.
4. [Activation Function]([[activation function]]): Determines whenever signal should progress through the network.
## How Neural Networks Learn
1. [[forward propagation]]: Input data moves through the network, later by later, until it reaches the output.
2. [[cost function]]: Measures the difference between the predicted and real value.
3. [[backpropagation]]: The error is propagated backwards through the network to adjust its weights and biases.
4. [[optimization function]] An algorithm that updates the parameters to minimize the loss.
## Advantages and Challenges
Advantages:
- Learns complex, non-linear relationships from data.
- Adapts to various types of data and problems.
- Can automatically extract features from raw data.
Challenges:
- Requires large amounts of data for training.
- Prone to overfitting if not regularized.
- Computationally intensive.
- "Black box" nature.