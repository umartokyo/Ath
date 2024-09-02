2024/09/01, #ML #tensorflow #wiki #umarik 

Tensorflow is a powerful library for [[machine learning, ML]] developed by Google. They've incorporated Keras library for easier use and prototyping within tensorflow. 
### TensorFlow vs +Keras:
| Feature           | Keras   | Tensorflow |
| ----------------- | ------- | ---------- |
| Easy to use       | Easy    | Difficult  |
| Training Speed    | Slow    | Fast       |
| Prototyping speed | Rapid   | Takes time |
| Debugging         | Easy    | Difficult  |
| Dataset needed    | Small   | Large      |
| Community         | Smaller | Bigger     |

---

Here's example code for implementing Tensorflow + Keras ML model for example of handwritten 10 digit classification:

```python
# Importing libraries
import numpy as np
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tetnsorflow.keras.activations import linear, relu, sigmoid

# Loading Dataset
X, y = load_data() # X.shape: (5000, 400), y.shape: (5000, 1)

# Specifying the Model
tf.random.set_seed(1234) # for consistent results
model = Sequential(
	[
		Dense(units=25, activation='relu'),
		Dense(units=15, activation='relu'),
		Dense(units=10, activation='linear'),
	], name = "handwritten digit classification"
)

# Compiling the model
model.compile(
	loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
	optimizer=tf.keras.optimizers.Adam(learning_rate=0.001),
)

# Training the model
history = model.fit(
	X, y, epochs=400
)

# Model summary
model.summary()

# Predicting
image = X[1234]
prediction = model.predict(image.reshape(1,400))
prediction_prob = tf.nn.softmax(prediction)
y_hat = np.argmax(prediction_prob)
```