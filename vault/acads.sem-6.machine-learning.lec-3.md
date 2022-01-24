---
id: SBDE29Uv1A941yOcaAtGZ
title: Lec 3
desc: ''
updated: 1643000616284
created: 1642922795725
---
## Overfitting and generalisation

- empirical risk can be rewrittena as:
- ![empirical risk](/assets/images/2022-01-17-11-44-05.png)
- $|D_{train}|$ is the size of training data $D_{train}$

<br>

- model that perfectly fits the training
data, but which is too complex - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">overfitting</code>

### Population Risk

- We assume that we have **_access_** to some distribution $p^*(x,y)$ but it is **_unknown_**
  - i.e. we can **_predict_** but not **_infere_**
- We define *theoretical expected loss* or <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">population risk</code> as:
- ![population risk](/assets/images/2022-01-17-11-57-17.png)
- difference between between population risk and the empirical lisk is defined as the <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">generalisation gap</code>
  - if a model has high *generalisation gap*, it is a sign of overfitting
  
<br>

- As we are only interested in the outcomes to find the *population risk*, we can divide the given data into **_train set_** and **_test set_**
- *Population Risk* can be then defined as
- ![PR on test set](/assets/images/2022-01-17-12-02-33.png)

### Choosing the Right Model

- ![Graphs](/assets/images/2022-01-17-12-11-11.png)
- [ ] [code](https://github.com/probml/pyprobml/blob/master/scripts/linreg_poly_vs_degree.py)
- from the fourth graph, we can see that as *degree of freedom* increases, the error on training set decreases
  - but the error on testing set follows a *U-shaped curve*
  - **Thus we should choose the data that minimizes the loss on test set**
- <blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em">In practice we divide the data into 3 parts<ul><li>validation data - for model selection</li><li>training data - for model training</li><li>testing data- for estimating the performance</li></ul> </blockquote>
