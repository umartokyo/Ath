2024/09/25, #ML #notes 

Root Node -> Decision Nodes -> Leaf Nodes

Decision Tree Learning
1. Picking Features
2. Dividing dataset into groups
3. Repeating previous two steps until we've arrived at leaf nodes.

**Key Decisions:**
- How to choose what feature to split at each node? (Maximize purity or minimize purity)
- When do you stop splitting? 
	- When a node is 100% one class.
	- When splitting a node will result in tree exceeding a maximum depth. (depth: number of splits we had so far) (Making a tree small will make it less prone to overfitting)
	- When improvements in purity score are below a threshold.
	- When number of examples in a node is below a threshold.

**Entropy  as a measuring of purity; Information theory :D**

Entropy is given by an equation:
$$p_1=\text{fraction of examples that are cats}$$
$$p_0=1-p_1$$
$$H(p_1)=-p_1log_2(p_1)-p_0log_2(p_0)$$
$$=-p_1log_2(p_1)-(1-p_1)log_2(1-p_1)$$

**Choosing a split: Information Gain**
Cat Examples:
Case1: Ear Shape
$$p_1=4/5=0.8, p_2=1/5=0.2$$
$$H(0.8)=0.72, H(0.2)=0.72$$
Weighted average: $$(\frac{5}{10}(H(0.8)+\frac{5}{10}H(0.2))$$
Information gain: (measures reduction in entropy) $$H(0.5)-(\frac{5}{10}(H(0.8)+\frac{5}{10}H(0.2))$$
$$=0.28$$
Case2: Face Shape
$$p_1=4/7=0.57, p_2=1/3=0.33$$
$$H(0.57)=0.99, H(0.33)=0.92$$
Weighted average: $$(\frac{7}{10}(H(0.57)+\frac{3}{10}H(0.33))$$
Information gain: $$H(0.5)-(\frac{7}{10}(H(0.57)+\frac{3}{10}H(0.33))$$
$$=0.03$$
We measure reduction in entropy because it will allow us to determine whether we want to prune the branch if reduction in entropy is too small.

**Information gain**
$$p_1^{\text{root}}=\text{number of positive examples in the root node}$$
$$p_1^{\text{left}}=\text{fraction of examples in left subtree with positive label}=4/5$$
$$w^{\text{left}}=\text{fraction of examples in left subtree in general}=4/5$$
$$p_1^{\text{right}}=\text{fraction of examples in right subtree with positive label}=4/5$$$$w^{\text{right}}=\text{fraction of examples in right subtree in general}=4/5$$
Information gain formula: $$H(p_1^{\text{root}})-(w^{\text{left}}H(p_1^{\text{left}})+w^{\text{right}}H(p_1^{\text{right}}))$$
We want to choose the feature division which will result in the highest information gain which will result in increase in the purity of subsets of data on both right and left branches of the tree.

**Decision Tree Algorithm**
Information gain criteria will help us chose which features to use for division of branches. 

- Start with all examples at the root node.
- Calculate information gain for all possible features, and pick one with the highest information gain.
- Split dataset according to select feature, and create left and right branches of the tree.
- Keep repeating splitting process until stopping criteria is met:
	- When node is 100% one class.
	- When splitting a node will result in the tree exceeding a maximum depth.
	- Information gain from additional splits is less than a threshold.
	- When number of examples in a node is below threshold.

Note that decision tree is recursive algorithm: each branch of it follows a pattern of the full tree. 

Increasing the maximum depth is the same as increasing the polynomials.
In theory, we could use cross-validation to pick hyper-parameters. In practice open-source libraries have better ways of choosing the max-depth and other parameters.

Making a prediction with decision tree takes just following the tree by going into the correct branch depending on the feature.

**Multi-class decision trees**
Here we'll look how we can use [[one-hot encoding]] to add multiple features to the tree.
For example, in the cat example, we might have 3 types of ear shapes instead of 2, which will divide our root node into 3 branches: pointy, floppy, oval. Instead, we can create a separate feature out of each ear type: does it have pointy ears? does it have floppy ears? does it have oval ears? It's called 'hot' encoding because only 1 of the features is hot, equals to 1.
> "" If a categorical feature can take on k values, create k binary values (0 or 1 valued).

**Decision trees with continuous values**
In a cat/dog classifier, we can add another feature, weight. But then how would we split our features into branches with continuous value?
We would plot a graph, where $x$=weight and $y$=cat/not cat. We would draw a vertical line and measure the entropy of it (fraction of cats and non-cats on the left...). In practice, we often measure the entropy for every line between every two consecutive parameters and choose the one with highest information gain. Using this, we can find an optimal value of weight as a splitting factor.

**Regression trees**
