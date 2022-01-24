---
id: BmxWSEoOhHxbfsbIbBBSN
title: Lec 2
desc: ''
updated: 1642922750442
created: 1642921088327
---
## Capturing Uncertainity

- in most of the cases, we can't predict perfectly due to:
  - *intrinsic(irreducible) uncertainity*: due to error in data collection...
  - *model uncertainity*: due to absence of infinite data / processing power
- We capture this uncertainity using conditional probability
- ![capturing uncertainity](/assets/images/2022-01-16-15-52-52.png)
- here $f: X \rightarrow [0, 1]^c$ maps the input to one of the $c$ labels
  - $f$ follows the axioms of probability:
    - $0 \leq f_c \leq 1$
    - $\textstyle\sum_{c=1}^n f_c = 1$
- [ ] restriction and <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">softmax function</code>
- [ ] <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">affine functions</code> and notations

## Maximum Likelihood Estimation

- A common loss function for probabilistic models is *negative log probability*
- ![NLP](/assets/images/2022-01-16-16-05-35.png)
- [ ] Intution and reason

### Negative Log Likelihood

- Averaging the of training set gives us <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">NLL</code>
- ![NLL](/assets/images/2022-01-16-16-07-48.png)

<br>

- If we minimize the *NLL*, we can compute maximum likelihood estimate of <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">MLE</code>
- ![MLE](/assets/images/2022-01-16-16-08-57.png)

# Regression

- *response* $Y$ is an continuous, real quantity

## Loss Function
- here the loss function is quadratic - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">l<sub>2</sub> loss</code>
- ![quadratic loss](/assets/images/2022-01-16-16-11-07.png)
- quadratic loss penalizes large *residuals* $y-\hat{y}$ more than small ones 
  - if the data has outliers, quadratic penalty can be very severe
  - in such cases we can use <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">l <sub>1</sub> loss</code>

## Empirical Risk

- Averraging the quadraticl log function, we get the mean squared error <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">MSE</code>
- ![MSE](/assets/images/2022-01-16-17-59-02.png)

### Negative Log Likelihood

- Fixing the variance for simplicity and using the $l_2$ loss function, we get *NLL* as:
- ![NLL](/assets/images/2022-01-16-18-08-38.png)
- this is proportional to MSE
  - **hence we can calculate maximum likelihood estimate by minmizing the MSE**
## Capturing Uncertainity

- In linear regression, output is assumed to *Gaussian* or *Normal*
- ![Gaussian](/assets/images/2022-01-16-18-02-12.png)
- Here the mean can be defined using the inputs, $\mu = f(x_n;\theta)$, and therefor the probability distribution is given by:
- ![dist](/assets/images/2022-01-16-18-05-09.png)
  
## Linear Regression

- <blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em">When we fit the data using <b>linear function of the parameters</b>, it is known as linear regression </blockquote>
- ![](/assets/images/2022-01-23-12-42-44.png)
  - [ ] [code](https://github.com/probml/pyprobml/blob/master/scripts/linreg_residuals_plot.py)
- we can fit a 1d data using a *simple linear regression* model of the form
- ![](/assets/images/2022-01-23-12-41-37.png)
- here $w$ is *slope* and $b$ is *offset*, and $\theta=(w,b)$ are the parameters of the model
- we minimize the squared error to get the least squares solution
- ![](/assets/images/2022-01-23-12-39-53.png)
- If we have multiple *predictors*, we can have a **_multiple lineare regression_**
- ![](/assets/images/2022-01-23-12-41-00.png)

## Polynomial Regression

- The fitting can be improved by using a **_polynomial regression_** model of the form $f(x;w) = w^T\phi(x)$
- $\phi(x)$ is a featue vector derived from the input 
- ![](/assets/images/2022-01-23-12-47-00.png)
- ![](/assets/images/2022-01-23-12-55-41.png)
  - [ ] [code](https://github.com/probml/pyprobml/blob/master/scripts/linreg_2d_surface_demo.py)
> It is important that the prediction function is a linear function of the parameter because a linear model induces a loss function $MSE(\theta)$ that has *unique global optimum*
