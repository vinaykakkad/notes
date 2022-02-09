---
id: thpLKumUhUP0f83D2CMWq
title: Lec 8
desc: ''
updated: 1644386683578
created: 1644211663972
---

# Model Fitting or Training

- estimating $\theta$ from a given data
  - we estimate it by minimizing the loss function $L(\theta)$

## Maximum Likelihood Estimation

- we pick the parameters that assign highest probability to the training data
- we define MLE as
- ![](/assets/images/2022-02-07-11-43-45.png)
- we assume that the training examples are independently sampled from the same distribution, ie <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">iid</code>(indpendent and identically distributed)
- the conditional likelihood then becomes
- ![](/assets/images/2022-02-07-11-50-56.png)
  - **_as the examples are independent, the overall probability can be expressed as the product of individual probabilities_**
- We use a log likelihood:
- ![](/assets/images/2022-02-07-11-54-31.png)
  - it is mathematically convenient to use log function as the likelihood can be expessed as summation
  - $log$ is a monotonically increasing function and provides one to one mapping
- The *MLE* is then given by:
- ![](/assets/images/2022-02-07-11-56-51.png)

<br>

- most of the cost functions are designed to *minimize* const function, we can redfine objective function to be a *negative log likelihood* or <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">NLL</code>
- ![](/assets/images/2022-02-07-11-58-41.png)
- minimizing this gives us the $\hat{\theta_{mle}}$

#### Optimal theta for unsupervised(unconditional) models

- as we only have outputs and no inputs in this case, MLE becomes
- ![](/assets/images/2022-02-08-08-02-15.png)
- alternatively, we can maximize the *join likelihood* of inputs and outputs. The MLE in this case becomes
- ![](/assets/images/2022-02-08-08-07-39.png)

### Example: MLE for Bernoulli distribution

- Y is $RV$ representing a coin toss
  - Y = 1 corresponds to heads
  - Y = 0 cooresponds to tails
- Let $\theta = p(Y=1)$ be the probability of heads
- MLE for such a *bernoulli dist.* can be given by:
- ![](/assets/images/2022-02-08-08-19-06.png)
- finding the derviative and setting it to 0, we get
- $\hat{\theta_{mle}} = \frac{N_h}{N_h + N_t}$, which is similar to intuitive result

<br>

- __Here we have not incoporated *population risk* and thus there is a high change of overfitting the training set__
  - The model in this case has enough parameters to perfectly fit the observed training data