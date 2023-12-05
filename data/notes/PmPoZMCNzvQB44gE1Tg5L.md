# Examplar based methods

- in *parametric* models, after estimating the parameters from the training data, we no longer need that data

<br>

- in *non-parametric* models, keep the training data
  - thus the effective number of parameters can grow with size of data $\lvert\lvert D \rvert\rvert$
- such models can be defined in terms of dissimilarity or distance function between a point in the testing set $x$ and that in the training set $x_n$ give by $d(x, x_n)$
- such approach is also called <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">instance-based</code> or <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">memory-based</code> learning

## KNN classification

- **_Assumption: similar datapoints have similar labels_**
- for a new input $x$, we look at the $K$ nearest neighbors and determine a probability distribution for the label
- ![](/assets/images/2022-02-02-02-02-47.png)
- there are two main parameters for *KNN* - number of neigbors $K$ and the distance function $D()$.  
- **_A small value of k leads to overfitting and a large value of k leads to uncerfitting_**

### choosing the optimal k

![](/assets/images/2022-02-02-02-06-50.png)
- [ ] [code](https://github.com/probml/pyprobml/blob/master/scripts/knn_classify_demo.py)
