
## Cross Validation

- when the data is very small, dividing into training, testing and validation set is not a good idea
  - very small sets can have a high bias
- we split the training data into **_K folds_**
  - in a round robin fashion, we train on all except one fold
  - ![](/assets/images/2022-02-16-11-56-07.png)
    - $R$ is the *regularized cross-validated risk*
    - $D_k$ is the data in k'th fold -> train for k'th fold
    - $D_{-k}$ is the data in k'th fold -> validate for k'th fold
- this is known as **_K fold cross validation_** or **_leave-one-out cross validation_**

<details>
<summary>schematic for 5-fold cross validation</summary>

![](/assets/images/2022-02-16-12-04-58.png)

</details>

- if the original data set has imbalance
  - use weighted strategy, by assigning high weightage to part will smaller size
- if cross validation causes imbalance
  - use [stratified cross validation](https://towardsdatascience.com/what-is-stratified-cross-validation-in-machine-learning-8844f3e7ae8e)

## Early Stopping - simple form of regularization

- many of the optimization are *iterative*, so they take many steps to move away from the initial parameter estimates
- if we detect signs of overfitting by monitoring the performance of validation set, we stop the optimization problem
- ![](/assets/images/2022-02-16-12-12-55.png)
- [ ] [code](https://github.com/probml/pyprobml/blob/master/scripts/imdb_mlp_bow_tf.py)
  
## Using More Data

- as the data increases, overfitting decreases(assuming the new data adds to the diversity and is not redundant)
- ![](/assets/images/2022-02-16-12-26-24.png)
  - black line is true error (noise with variance 4), we cannot go below it -> <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">noise floor</code>
  - for a small degree, the error always remains high -> *undefitting*
  - test error decreases for other models, but it reduces more rapidly for simpler models
  - *generalization gap* is initially larger for complex model, but decreases as size grows
  