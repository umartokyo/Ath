2024/07/31, #ML #wiki #umarik 

Supervised learning is a type of [[machine learning, ML]] where algorithm trains from labeled training data to predict the target value. The dataset typically includes pairs of inputs and outputs where input is data point and output is corresponding label or desired value. 

Two major types of supervised learning are: [[regression]] and [[classification]]. The difference between them being that regression predicts a value out of infinite set (e.g., house prices), while classification predicts from a finite set of categories (e.g., spam or not?).

Mathematically, supervised learning can be viewed as finding function $f(x)$ that maps input $x$ to output $y$:

$$f(x)=y$$

Training process involves calculating optimal parameters of the function to minimize the cost $J(\theta)$:

$$J(\theta) = \frac{1}{2m} \sum_{i=1}^{m}(h_\theta(x^{(i)}) - y^{(i)})^2$$

where $m$ is the number of training examples, $h_{\theta}(x)$ is the hypothesis function, and $y^i$ is the target value for the example $i$. (Squared error cost was used in this example.)