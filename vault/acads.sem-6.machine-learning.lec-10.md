---
id: o9V4uumi3Tls8uGzJEcos
title: Lec 10
desc: ''
updated: 1644951005537
created: 1644818744038
---
## Approaches for Machine Learning

- *frequentist* ($P(D;\theta)$)
  - find such a $\theta$ that maximizes that given data
  - this approach does not consider $\theta$ as a random variable
    - i.e. the value of parameters does not depend on any prior event
- *bayesian statistics* ($P(D|\theta)$)
  - in this approach the value of params depends on prior knowledge
    - $P(\theta)$ can be encoded as a distribution
      - i.e. prior knowledge can be incoporated in the distribution

## Weight Decay

- using regression with very high degree of polynomial results in overfitting
  - we tried to reduce the degree of polynomial to generalize the model
- another solutions is to penalize the magnitude of weights(*regression coefficients*)


<br>

- we use a *zero-mean Gaussian* prior to penalize the weights, and the resulting MAP is given by
- ![](/assets/images/2022-02-16-00-09-17.png)
  - here we use $w$ instead of $\theta$, since we only penalize the weight vector and not bias terms or noise variances
- this is called <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">l<sub>2</sub>regularization</code> or **_weight decay_**
- in case of linear regression, this kind of penalization scheme is called <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">ridge regression</code>

## Finding the optimal regularization parameter

- picking a small $\lambda \implies$ focussing on minimising empirical risk $\implies$ *overfitting*
- picking a large $\lambda \implies$ focussing on prior $\implies$ *underfitting*
- we use validation set to find the optimal $\lambda$

![](/assets/images/2022-02-15-23-59-38.png)

- [ ] [code](https://github.com/probml/pyprobml/blob/master/scripts/linreg_poly_ridge.py)


# TODO

- [ ] bias variance dilemma
- [x] finding validation method for small data
  - cross validation