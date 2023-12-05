
# Solutions to overfitting - Regularisation

- we introduce an additional parameter $\lambda$, which is the *regularisation* parameter or a penalty term
- ![](/assets/images/2022-02-09-11-33-47.png)
  - $\lambda \geq 0$ is regularization parameter
    - assigns weight to the *penalty* or *bias*
  - $c(\theta)$ is some form of complexity penalty
    - a common penalty is $C(\theta) = -\log p(\theta)$, where $p(\theta)$ is the prior probability for $\theta$
    - **_we assume that we have some prior knowledge about the problem_**
- if $l$ is the negative log loss, the reguralised objective becomes
- ![](/assets/images/2022-02-09-11-43-41.png)
- setting $\lambda=1$ and rescaling $p(\theta)$, we minimize the following
- ![](/assets/images/2022-02-09-11-45-16.png)

<details>
<summary>minimizing this objective is equivalent to maximizing the posterior log</summary>

- in *MLE*, we do not consider any prior knowledge and we tweak $\theta$ to optimize - $P(D | \theta)$
- the prior knowledge about the parameter can be expresses as - $P(\theta)$
- to incorporate this prior knowledge, we find the posterior porbability $P(\theta | D)$
  - using the bayes theorem, $P(\theta | D) = \frac{P(D | \theta)P(\theta)}{P(D)}$
  - applying the log, we can get the equation described in the next step

</details>

- ![](/assets/images/2022-02-09-11-51-24.png)
- this is known as <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">MAP</code> (*maximum a posterior estimation*)

## Bernoulli Example with Regularisation

- to avoid overfitting, we introduce *prior* $p(\theta)$ as a <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">beta distribution</code>

<details>
<summary>beta distribution</summary>

- ![](/assets/images/2022-02-09-12-03-48.png)
- based on the values of a and b, we get different plots for the beta distribution
- for a, b > 1, we get a dsitribution similar to the purple one, which discourages extreme values of theta like 0 or 1

</details>

- the log likelihoo plus the log prior becomes
- ![](/assets/images/2022-02-09-12-09-02.png)
- to find the maximal value, we differentiat and set it 0, to get the value of $\theta_{map}$
- ![](/assets/images/2022-02-09-12-11-12.png)
- setting a = b = 2, which favous the value of $\theta = 0.5$
- ![](/assets/images/2022-02-09-12-11-57.png)
- this is known as *smoothing of frequentist approach*