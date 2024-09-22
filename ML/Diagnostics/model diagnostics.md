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
It hardly ever hurts to have a larger neural network as long as you regularize it appropriately; as long as training set is not too large, your NN is low bias machine.

## Iterative Loop of ML development
- Choosing model architecture (model, data, hyper-parameters)
- Train model
- Diagnostics (bias, variance and error analysis)

Example: Building a spam classifier
Supervising learning: $\vec{x}$ = features of email; $y$ = spam (1) or not spam (0)
We  can list the top $10,000$ words to compute $x_1,x_2,...x_{10,000}$ to count but setting them just to be 1 or 0 would work decently well too. Given these feature we can train logistic regression model or a neural network to predict $y$ given features $z$. It it doesn't work, we can try:
- Collecting more data.
- Develop sophisticated features based on email routing. (sequence of computer services the email have gone through: email header)
- Define sophisticated features from email body. ("discounting" and "discount" can be treated as the same word.)
- Design algorithms to detect misspellings. (w4tches, med1cine...)
## Error Analysis
If there's a list of the most important types of model diagnostics, variance / bias would be on the first place and error analysis on second. 

Error Analysis: Manually looking through the examples in cross validation set where the algorithm does something wrong. Try group misclassified data by common behavior of those data points, count them up. Afterwards, you can prioritize the highest error categories. You can improve your model by making specific changes to the algorithm concerning the category with most errors, add more datapoints of this category or try something else. After error analysis, you can find a new approach to the architecture: model, dataset and so on.
## Adding Data
Sometimes it's more tempting adding more data of every kind, which often results in poor performance. It's better to add data of the types where error analysis has indicated it might help. We could go to unlabeled data and find more examples of the error category we need. 

If you have some way to add more data of everything - that's okay. But you want to add more data after error analysis, getting more data of the types you need would be more efficient way of adding a bit more data to boost algorithm's performance by a lot. 

Data Augmentation: You can also create new training examples by modifying existing training examples to create a new training example. (Ex: You can distort the letter image by changing color, size, rotation, blurriness, mirroring, warping...) It also works for speech recognition. You can add noisy background audio to the original audio clip or add effects to it. Using data augmentation, you can artificially boost the dataset size, but you have to keep track of the distortions made within the dataset. Adding random noise to the image is not helpful. 

Data Synthesis: You generate an entire dataset. For example, for photo OCR, you could just take all fonts from your machine, change text, color, font, size... of the text and take screenshots to create a new dataset, which would look pretty realistic. (Synthetic data generation is most commonly used for computer vision tasks.)

These are ways of engineering the data used by your system.
**Conventional model-centric approach**: AI = *Code* + Data (researchers are trying to improve code of the model.)
**Data-centric approach**: AI = Code + *Data* (you focus on the data fed into your model.)
## Transfer Learning
Transfer learning: using data from different task.
**Supervised pre-training**: Training on the larger data-set beforehand to train final model with better initial parameters. (We hope the algorithm learns the basics of image recognition by this.)
**Fine tuning**: You train your model further on the actual dataset to get the weights to suit your case. 
Nice thing about transfer learning is that you don't have to be the one to do the supervised pre-training, but just download the parameters someone else have trained to quickly move on to fine-tuning the model to the your task.

Why does transfer learning work?
If you are training a computer vision model to recognize the objects on the image, your model's 1st layer might learn to find edges of the image, second layer for corners, and third for curves / basic shapes. By training a model to detect cats, dogs, humans, cars, bicycles... we train them to recognize these basic shapes which is the first step to recognizing digits as well.
However, you have to pre-train the model with the same type of data as you'll use. (image of desired dimensions, audio, text...)

Transfer learning summary:
1. Download / Train neural network parameters pre-trained on a large dataset with the same input type as your application.
2. Further train (fine tune) the network on your own data.
## Full Cycle of Machine Learning Project
Example: Speech recognition.
1. Scope project (define project)
2. Collect data (define and collect data)
3. Train model (training, error analysis & iterative improvement) (might return to step 2)
4. Deploy in production (deploy, monitor and maintain system)

Deployment:
We implement an inference server where we deploy our ML model. Afterwards, a mobile app makes an API call (sends audio clip) and gets inference (text transcript). To implement this, you might need some software engineering to ensure reliable and efficient prediction, scale, log, monitoring the system and updating the model.
MLOps: Machine Learning Operations, software engineers who take care of model deployment.
## Fairness, bias, and ethics
Examples:
- Hiring tool that discriminates against women.
- Facial recognition system matching dark skinned individuals to criminal mugshots.
- Biased bank loan approvals.
- Toxic effect of reinforcing negative stereotypes.
Adverse use cases:
- Deepfakes.
- Spread of toxic/incendiary speech through optimizing for engagement.
- Generating fake content for commercials or political purposes.
- Using ML to build harmful products, commit fraud, etc.
- Spam vs anti-span.
Please do not work on unethical projects.

**Guidelines**:
- Before deploying a model, get a diverse team of red hats to search for possible harms / vulnerable groups of your project.
- Carry out literature search on standards / guidelines for your industry.
- Audit system against possible harm prior to deployment. (check if the problem brainstormed by red hats does really exists by auditing the model after training the model.)
- Develop mitigation plan (if applicable), and after deployment, monitor for possible harm.
## Error metrics for skewed datasets
Skewed: the ratio of positive and negative examples in your dataset is far from 50/50 in classification model. Usual error metrics like accuracy might not work well.
Example: In rare disease classification example, there might be only 1% of the sick patients in the dataset, meaning model identifying 99% correctly would be worse than just a print statement. That's why we won't use statistical 'accuracy' as a benchmark in machine learning. 
**Precision / Recall**: $y=1$ in presence of rare class we want to detect.

| Confusion Matrix  | Actual Class 1     | Actual Class 0    |
| ----------------- | ------------------ | ----------------- |
| Predicted Class 1 | True positive: 15  | False positive: 5 |
| Predicted Class 0 | False negative: 10 | True negative: 70 |
**Precision**: $\frac{True Positives}{\text{num of predicted positive}} = \frac{True Positives}{True Pos + False Pos}$, of all patiences, where we predicted $y=1$, what fraction actually have the rare disease? In our case: $\frac{15}{15+5}=0.75$.
**Recall**: $\frac{TruePos}{NumOfActualPos} = \frac{TruePos}{TruePos+FalseNeg}$, of all patients that actually have the rare disease, what fraction did we correctly detect as having it? In our case: $\frac{15}{15+10}=0.6$.
An algorithm with zero precision or zero recall is not a useful algorithm.
When you have a rare class, look at precision and recall and if the values are decently high, you're on a right track of building a useful model.
## Trading off Precision and Recall
There's often a tradeoff between precision and recall. In logistic regression, you can raise a threshold of predicting whenever a patient is sick to from $0.5$ to $0.7$ to increase precision which will lower recall. This might be useful if that is a non-important costly disease. On the flip side, if the disease is important, we could lower the prediction threshold to increase recall while lowering precision. It will predict the disease for people with slightest chance of having it.
Precision x Recall graph looks like a top-right part of the circle of radius 1 with the center on $(0,0)$.
You'll most likely end up manually picking it. There's also F1 Score to automatically combine precision and recall. If you end up having couple models with various precisions (P) and recalls (R), you can combine them through $F_1$ score. Higher the $F_1$ score, the better the algorithm.
$$F_1{score}=\frac{1}{\frac{1}{2}(\frac{1}{P}+\frac{1}{R})}=2\frac{PR}{P+R}$$
.