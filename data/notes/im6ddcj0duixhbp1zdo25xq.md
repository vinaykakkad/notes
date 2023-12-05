- non parameterized supervised learning algorithm
- we divide the predictor space into number of simple regions
- prediction is made on the basis of some statistic of these regions
- decision trees are easier to interpret, but its performance is not competitive with other algorithms
  - bagging, boosting, random forests are used to improve performance

## Regression Trees

- we divide predictor space (data: $X_1, X_2, ... X_p$) into $J$ distinct non-overlapping regions($R_1, R_2, ... R_j$)
- for each region we make the same prediction: **mean** or **median** of that region

### How to construct the regions

- we try to minimize the objective
- ![](/assets/images/2023-01-16-15-43-31.png)
- we use `recursive binary splitting`
  - i.e. at every point we try to divide a particular space around a cutpoint $s$: $\{X| X_j < S\}$ and $\{X| X_j > S\}$
  - there are [ways](https://mlcourse.ai/book/topic03/topic03_decision_trees_kNN.html#how-a-decision-tree-works-with-numerical-features) to define a set of cutpoints
  - we find a cutpoint such that the sum of objective in the sub-regions is minimzed

#### Overfitting and Tree Pruning

- we first build a very large tree
- we use cross validation to find subtrees that minimze the test error
- we introduce $\alpha$ -- the complexity parameter
  - for every value of alpha there is a subtree such that the objective is minimum
  - ![](/assets/images/2023-01-16-16-31-27.png)
  - $|T|$ indicates the number of terminal nodes
- when $\alpha$ is 0, we get the original large tree
- but as $\alpha$ increases, branch gets pruned from tree in a nested and predictable fashion

- we then figure out the optimal alpha using cross validation

## Classification Trees

- same approach as regression trees
  - final prediction is based on the most occurring class in the region

### Error functions for classification trees

- mis classification rate
- ![](/assets/images/2023-01-16-16-39-45.png)
  - $p̂mk$ = proportion of training observations in the mth region that are from the kth class
- gini index
  - ![](/assets/images/2023-01-16-16-49-06.png)
- entory
  - ![](/assets/images/2023-01-16-16-49-18.png)
- gini index and entropy are both related to variance and show similar results
