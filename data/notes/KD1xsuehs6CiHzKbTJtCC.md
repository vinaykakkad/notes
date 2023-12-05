# Pillars of the course

- classifcation
- regression
- dimensionality reduction
- clustering

# What is machine learning

John Mitchell' definition
<blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em">A computer program is said to learn from an experience <b>E</b>, with respect to some task <b>T</b> and using some performance measure <b>P</b>, if its pefromance improves with experience
</blockquote>

# Probabilistic approach for ML

- treat every unknown quantity as a <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">RV</code>
- use different proability distributions to model that uncertainity
- we use probabilistic approach because:
  - it is optimal decision making strategy under some uncertainity
  - other areas of science and engineerig also use the same approach

# Supervised Machine Learning

- data with outputs corresponding to inputs is provided
- we try to find the mapping between theese inputs and outputs

## Classification Problem

- output space is a set of c *distinct* and *mutually exclusive* <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">labels</code>
- output is a *categorical variable*
- the problem is also called <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">pattern recognition</code>

### IRIS flowers dataset

- labels:
  1. setosa
  2. versicolor
  3. virginica
- featues:
  1. petal length
  2. petal width
  3. sepal width
  4. sepal length

- In cases similar to this, when the size is fixed, the data is stored using <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">design matrix</code>
- Such a dataset is <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">tabular data</code>
- when the inputs are of variable size we may need to store the data in some other format

![Pairwise Scatter Plot for Iris Dataset](/assets/images/2022-01-14-23-01-57.png)
- pairwise scatter plot for iris dataset
- the diagonal shows the probability distribution for that particular *predictor*
- from this we can get intution for decision rules
  - ex: if petal length exceeds some limit, it won't be of a particular type
- [ ] [code for the scatter plot](https://github.com/vinaykakkad/pyprobml/blob/master/scripts/iris_plot.py)

### EDA note

- for such datasets with very few predictors, it is common to plot such pair plots to get the intution
- for datasets with high number of predictors, <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">dimensionality reduction is performed</code>
  
![Decision Tree](/assets/images/2022-01-14-23-11-37.png)
- decision tree for the iris dataset
- [ ] [code_1 for decision tree](https://github.com/vinaykakkad/pyprobml/blob/master/scripts/iris_dtree.py)
- [ ] [code_2 for decision tree](https://github.com/vinaykakkad/pyprobml/blob/master/scripts/iris_dtree2.py)

# Empricial(experimental) Risk Minimisation

## Missclassification Rate

- in the above example, error in the model can be expressed as missclassifcation rate which is given by:
- ![Misclassification Rate](/assets/images/2022-01-16-14-05-56.png)
  - $\theta(parameters)$ are the decision rules that we make 
  - in case of linear regression, $\theta$ are the weights that we assign to the predictors
- Here $I(e)$ is the binary indicator function, which return when the output return by our model does not match the actual output
- ![Indicator function](/assets/images/2022-01-16-14-07-57.png)

<br>

- here we assume that each incorrect prediction has the same loss
- in general, we can define a <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">loss function</code>, which is a function of the predicted output and actual output on the training set
- the *empirical risk* is then defined as:
- ![Empirical Risk](/assets/images/2022-01-16-14-22-51.png)

## Model Fitting or Training

- one way is to find $\theta$ that minimize the empirical risk (*empirical risk minimization*)
- ![ERM](/assets/images/2022-01-16-14-31-19.png)
- true goal: *minimize the loss on future data* - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">generalization</code>

# TODOs

- [ ] ISLR

- [ ] Random Variables
- [ ] Tranformation of RVs
- [ ] Diff probability distribution
