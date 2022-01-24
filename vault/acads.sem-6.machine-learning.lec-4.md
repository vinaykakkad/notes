---
id: Rh3CSk5AzxljaDfFQC5wQ
title: Lec 4
desc: ''
updated: 1642997952584
created: 1642923168514
---

# Bias Variance Tradeoff

- ![](/assets/images/2022-01-23-13-19-15.png)

## Bias

- average of the difference between the true values and the predicted values
- it means:
  - very little attention to training data
  - oversimplification of model
- *high bias corresponds to underfitting*

## Variance

- models with high variance pays a lot of attention to training data and does not *generalize*
- *high variance corresponds to overfitting*

# No Free Lunch Theorem

- <blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em">There is no single model that workd optimally for all kinds of problems</blockquote>
- i.e. if we find the average performance of a model over all possible problems, then there is no single model that outperforms every other models