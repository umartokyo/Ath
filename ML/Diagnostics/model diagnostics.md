2024/09/02, #ML #wiki #main #umarik 

After training a [[machine learning, ML]] model, you might want to evaluate its performance using various methods and tools. Here we'll discuss about it. 
## Evaluating a Model
Division of the dataset into training set and test set (70/30 or 80/20) so we can evaluate the model on the dataset it hasn't seen before.
- training set: $m_{train}$ number of training examples
- test set: $m_{test}$ number of testing examples
Notice that after you run a cost function for both training and test set and if the loss if will low on training set but high on test set; your model is overfitting. Training error is nearly non-existent and model gets lost in new data.  (note that you don't need a [[feature regularization]] term in test set version of loss function) If the model would estimate correcting the testing data and generalize correctly, the model is considered good.

Here's how it would look like for Linear Regression with squared error cost:
Fit parameters by minimizing cost function $J(\vec{w},b)$:
$$J(\vec{w},b)=[\frac{1}{2m_{train}}\sum^{m_{train}}_{i=1}{f_{\vec{w},b}(\vec{x}^{(i)}-y^{i})^{2}+\frac{\lambda}{2m_{train}}\sum^n_{j=1}{w^2_j}}]$$
Compute test error:
$$J_{test}(\vec{w},b)=\frac{1}{2m_{test}}[\sum_{i=1}^{m_{test}}(f_{\vec{w},b}(\vec{x}^{(i)}_{test})-y^{(i)}_{test})^2]$$
Compute training error:
$$J_{train}(\vec{w},b)=\frac{1}{2m_{train}}[\sum_{i=1}^{m_{train}}(f_{\vec{w},b}(\vec{x}^{(i)}_{train})-y^{(i)}_{train})^2]$$

In summary, we're creating a list of the possible models which might match well with our dataset, and training each of these models on some subset of data we allocate to them to check on their performance and choose a final model to train the whole test set on.
## Model Selection
After training our model, the training error might be lower than the actual error. (as model might overfit). That's why we use $J_{test}(\vec{w},b)$ for better estimate of how well will the model generalize for the new data compared to $J_{train}(\vec{w},b)$. 

1. $d=1|f_{\vec{w},b}(\vec{x})=w_1x+b \rightarrow w^{<1>},b^{<1>} \rightarrow J_{test}(w^{<1>},b^{<1>})$
2. $d=2|f_{\vec{w},b}(\vec{x})=w_1x+w_2x^2+b \rightarrow w^{<2>},b^{<2>} \rightarrow J_{test}(w^{<2>},b^{<2>})$
3. $...$

After training each of these models, you might find out that $J_{test}(w^{<5>},b^{<5>})$ will be the lowest and $d=5$ is the best model. To estimate how well this model performs, you could report a test set error $J_{test}(w^{<5>},b^{<5>})$, which might be flawed as it might be optimistic estimate of generalization error. It might be lower than actual generalization error as we've chosen the model which performs best in the test set and fit our parameter $d$ into our training set. (training set is supposed to be used only for the evaluating of the model, and be out of reach during the process of training our model.)
### Best method
Due to this reason, we want to divide our data set into 3 sets:
1. Training Set: ~60% of data; used for training the model.
2. Cross Validation Set: ~20% of data; used for choosing hyper-parameters and architectures.
	- aka "validation set", "development set", "dev set"
3. Test Set:  ~20% of data; used for evaluating general loss.

With this update, you can now compute training error, cross validation error and test error by changing the data set from test the earlier examples.  Now we can train the models as earlier but now instead of evaluating the models on test set, we change it to cross validation set for evaluation.
1. $d=1|f_{\vec{w},b}(\vec{x})=w_1x+b \rightarrow w^{<1>},b^{<1>} \rightarrow J_{cv}(w^{<1>},b^{<1>})$
2. $d=2|f_{\vec{w},b}(\vec{x})=w_1x+w_2x^2+b \rightarrow w^{<2>},b^{<2>} \rightarrow J_{cv}(w^{<2>},b^{<2>})$
3. $...$

Pick $d$ with lowest $J_{cv}$, afterwards you can estimate generalization error using the test set $J_{test}(w^{<4>},b^{<4>})$. Now and only now, our generalization error with test set can be taken as valid.

This procedure can be used in choosing the [[neural network]] architecture too. We could train our model's parameters $\vec{w},b$ to fit the training set, then evaluate their performance on cross validation set to pick the best model for our case. Afterwards, to get the generalization error we can test our model on the test set. 

This method works both for choosing model architecture, hyper-parameters using the training and cross validation set. After coming up with our final model, we're using test set to get the general loss.
## Bias and variance
High Bias (aka under-fit): 
- $J_{train}$ is high
- $J_{cv}$ is high
Just Right:
- $J_{train}$ is low
- $J_{cv}$ is low
High variance (aka overfit):
- $J_{train}$ is low
- $J_{cv}$ is high

To find the "just right" trained model, you must find the lowest point of function $J_{cv}$ which resembles positive parabola, and balance it with the negative exponential function of cost $J_{train}$. As there are more polynomials or parameters, $J_{cost}$ becomes smaller and smaller yet $J_cv$ will be getting bigger and bigger as the model will overfit the data. And if there are not enough parameters or polynomials, model will under-fit showing us both high $J_{train}$ and $J_{cv}$.

There might be a case where you've somehow achieved both high bias and high variance but it's pretty rare. You can identify it when your $J_{train}$ is very high but $J_{cv}$ is even higher.
## Regularization and bias / variance
How does the choice of parameter $\lambda$ affect the performance of our model?

For [[feature regularization]], if we set our $\lambda$ very large, the algorithm is motivated to keep our parameters very small (close to zero) so our algorithm ends up being just $b$, straight line.

High bias $\rightarrow$ high bias, under-fit

On the other hand, if $\lambda$ is very small, our polynomial is being fit with almost no regularization and we get our squiggly curve that over-fits the data.

Low bias $\rightarrow$ high variance over-fit

If you get just right value of $\lambda$ for regularization parameter, you can use our cross-validation method with partial dataset. We train a model with list of different lambdas on our training set to later evaluate their performances with cross-validation set and choose the best-performing $\lambda$. If you plot a graph with $x=\lambda,y=J_{train}$, you'll get the exponential function. Additionally, if you fit another function $y=J_{cv}$, it will look like happy parabola. Again, we're trying to find a lowest point of the cross-validation parabola.
## Establishing baseline performance
Establishing baseline performance is giving some basic expectations from model's performance. Baseline performance can be predicted in three main ways:
1. **Human performance**: You evaluate what's the human performance in doing the task and striving to close the gap between human and model performance.
2. **Competing algorithm performance**: Taking your competitors' performance as a baseline performance for your model is another method of evaluation.
3. **Guess based on experience**: Sounds as called, if you've trained this kind of models before you might have remembered the performance of those and can use it as the baseline performance for your new model.

| Error type                      | High Variance | High bias | High variance & bias |
| ------------------------------- | ------------- | --------- | -------------------- |
| Baseline performance            | 10.6%         | 10.6%     | 10.6%                |
| Training Error $J_{train}$      | 10.8%         | 15.0%     | 15.0%                |
| Cross validation error $J_{cv}$ | 14.8%         | 15.5%     | 19.7%                |
Bias / Variance examples.
## Learning Curves
$$p=m \times v \cdot o \div u$$
