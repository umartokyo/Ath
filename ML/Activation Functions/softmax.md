2024/08/22, #ML #wiki #umarik 

Softmax is a generalization of [[logistic, sigmoid]] or [[logistic regression 1]] algorithm to the [[multi-class classification]] contexts. 

$$y, j=1,2,3...N$$
$$z_j=\vec{w_j}*\vec{x}+b_j$$
$$a_j=\frac{e^{z_j}}{\sum^N_{k=1}e^{z_k}}=P(y=j\mid\vec{x})$$

Note that sum of all $a_j$'s will always add up to 1.
Additionally, if $j=2$, softmax generally computes same thing as sigmoid.

cost function:
$$
loss([a_1,...a_N], y)= \begin{cases} 
-log(a_1) & \text{if } y = 1 \\
-log(a_2) & \text{if } y = 2 \\
... \\
-log(a_N) & \text{if } y = N 
\end{cases}
$$
$$loss=-log(a_j),\; \text{if}\; y=j$$

Note that each training example can optimize with respect to only single parameter, which is the case where $y=j$.

Notice how unlike other [[activation function]]s, where for each output, we take single inputs and return an output with respect to it, in the softmax algorithm, for each output we take the whole previous row as inputs and return a single output with respect to all inputs. This property is unique to the softmax algorithm / function.