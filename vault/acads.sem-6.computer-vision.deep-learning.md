---
id: 7iwle7bwr3wgmqx19n1i3sh
title: Deep Learning
desc: ''
updated: 1652029489346
created: 1651560141913
---

# Beyond Linear Mapping

- a simple way to increase flexibility -> *Feature Transformation*
  - still linear in term of params -> fitting easy
  - but manual feature transformation is very limiting and requires very strong domain knowledge

- modelling the feature extactor to increase flexibility
$$
f(x, \theta) = W\phi(x;\theta_{2}) + b
$$
- $\theta = (\theta_1, \theta_2)$ and $\theta_1 = (W, b)$
- reursively repeating the process to create complex functions
$$
f(x, \theta) = f_L(f_{L-1}(...f_1(x)...))
$$
  - key idea behind deep neural networks
  - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">DNN</code>
    - mapping input to output using DAG(directed acyclic graph) of functions
    - also known as **_feed forward network_** or **_multi layer perceptron_**
    - CNN for images, RNN for sequences, GNN for graphs

# Multi Layer Perceptron

- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">perceptron</code> - heavyside step function or linear threshold function
$$
f(x;\theta) = I(w^T + b \geq 0) = H(w^T + b)
$$

- as decision boundaries are linear, represntation is very limiting
  
<details>
<summary>for simple XOR, we need multiple layers</summary>

![](/assets/images/2022-05-03-17-27-14.png)

</details>

## Importance of depth

- depth helps in hierarchial feature extraction
- deeper layers can leverage the learning of previous layers

# ANN and Neuron Structure

![](/assets/images/2022-05-08-08-08-26.png)

# Learning

## Gradient Descent

- iterative optimization algo for finding minima
- **_idea_**: repeated steps in the direction opposite to the graident at current point

## Batch gradient descent

```python
weights = initialize_random_weights(shape)

for _ in range(epochs):
  average_gradient = find_average_gradient(data, loss_fn, weights)
  weights = weights - learning_rate * average_gradient
```

## Stochastic gradient descent

```python
for _ in range(epochs):
  data = shuffle_data(data)
  for row in data:
    row_gradient = find_row_gradient(row, loss_fn, weights)
    weights = weights - learning_rate * row_gradient
```

## Mini-batch graident descent

```python
for _ in range(epochs):
  data = shuffle_data(data)
  for batch in get_batches(data, batch_size):
    batch_gradient - find_batch_gradient(batch, loss_fn, weights)
    weights = weights - learning_rate * batch_gradient
```

<details>
<summary><b><i>Comparison</i></b></summary>

### Loss Plots
![](/assets/images/2022-05-08-10-56-40.png)

### Properties
![](/assets/images/2022-05-08-10-57-13.png)

</details>


## Problems in Descent

1. learning rate pace
   - learning rate low -> slow convergence
   - learning rate high -> fluctuations and overfitting

2. imbalanced data
   - if the data has features with different frequencies
     - cannot apply same learning to all features
     - need high learning rate for rare features
   - loss changes quickly in one direction and slowly in other

3. non-convex loss functions
   - suboptimal **local minimas**
   - **saddle points**(one dimension slopes up another slopes down)
      - surrouded by plateau of same error, difficult to escape
   - **cliffs** in RNN

4. NNs
   - vanishing and exploding gradients

## Solutions

### Momentum

- helps to accelerate descent in relevant
- reduces oscillations
- **_idea:_** take a fraction of past updates
  - momentum at time t: $v_t = \gamma v_{t-1} + \eta \frac{\delta J(W)}{\delta W}$
  - Update: $W = W - v_t$
  
<details>
<summary>explanation</summary>

![](/assets/images/2022-05-08-12-04-59.png)

- consider the following example
  - here the gradient in vertical direction is oscillating
  - in horiontal direction is approaching optimum
- if we take the sum of previous gradients:
  - oscillation in vertical direction will cancel out
  - velocity in horizontal direction builds up

</details>

### Neterov Accelerate Gradient

- prevents us from going too fast and overshoot
- **_idea:_** take gradient at future value for calculating momentum
  - momentum at time t: $v_t = \gamma v_{t-1} + \eta \frac{\delta J(W - \gamma v_{t-1})}{\delta W}$
  - Update: $W = W - v_t$

<details>
<summary>illustration</summary>

![](/assets/images/2022-05-08-12-16-46.png)

</details>

### AdaGrad

- $S = \sum \frac{\delta J(W)}{\delta W}$
- Update: $W = W - \eta \frac{\delta J(W)}{\delta W} * \frac{1}{\sqrt{S + \epsilon}}$
  - over a batch / mini-batch  
- makes learning slow for predictors with high gradient
- makes learning fast for predictors with low gradient

### Regularization

- to avoid overfitting, punish the complexity
- adding a regularization term to the objective / loss function

![](/assets/images/2022-05-08-16-50-09.png)

- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">L2 regularization</code> -> $R(W) = \sum\sum W_{k, l}^2$
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">L1 regularization</code> -> $R(W) = \sum\sum | W_{k, l} |$
- <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">L1 + L2 regularization</code> -> $R(W) = \sum\sum \beta W_{k, l}^2 + | W_{k, l} |$

### Dropouts

- standard practice: dropout 50% of the neurons
- at each epoch the random 50% changes and thus, the chance of a neruons overfitting decreases

# Backpropogation

- [ ] [Backpropagation Step by Step](https://hmkcode.com/ai/backpropagation-step-by-step/)
# Activation Functions

- purpose -> to introduce non-linearity in the network
  - using a linear function will just give us a line in n-dimension
  - ![](/assets/images/2022-05-08-07-50-23.png)

## Some common activation functions
  
### Sigmoid

- smoothing of heaviside function
- between 0 and 1
- gets saturated at extreme values

### tanh

- similar nature as sigmoid
- between -1 and 1

### ReLU

- piecewise linear
- solves the problem of vanishing graidents in sigmoid and tanh


# Automatic Differentiation and Computational Graphs

- dl frameworks provide *autograd*
- mainatain a <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">computation graph</code>
  - directed graphs describing the flow of data
  - breaks the functional chains in the form of a graph
  - [ ] [How Computational Graphs are Constructed in PyTorch](https://pytorch.org/blog/computational-graphs-constructed-in-pytorch/)
    - [ ] [Pytorch Autograd](https://pytorch.org/blog/overview-of-pytorch-autograd-engine/)
    - [ ] [Understanding accumulated gradients in PyTorch](https://stackoverflow.com/questions/62067400/understanding-accumulated-gradients-in-pytorch)