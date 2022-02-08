---
id: stO81oij4841YX11cSuZI
title: Lec 7
desc: ''
updated: 1644285940794
created: 1643780631948
---
# Multivariate Models

- measure of dependence of one $RV$ on others
  
## Covariance

- measures the degree of linearity(dependency) between two *random variables*
- ![](/assets/images/2022-02-02-11-40-37.png)
- for higher dimension, we define a *covariance matrix* $\Sigma$
- ![](/assets/images/2022-02-02-11-44-24.png)
  - covariance matrix is **_positive definite symmetric matrix_**  
    - easy to perform eigenvalue decomposition and the eigenvalues are real
  - range is $[-\infty, \infty]$

### Imortant Properties

- ![](/assets/images/2022-02-07-18-39-14.png)
- ![](/assets/images/2022-02-07-18-39-35.png)
- ![](/assets/images/2022-02-07-18-40-00.png)

## Correlation(degree of linearity)

- normalizing the covariance, we get *(Pearson) __correlation coefficient__*
- ![](/assets/images/2022-02-07-18-41-50.png)
  - range is $[-1, 1]$
<details>
<summary>correlation matrix</summary>

![](/assets/images/2022-02-07-18-44-05.png)

</details>

- ![](/assets/images/2022-02-08-07-21-24.png) 
  - $Corr[X, Y] = 1 iff Y = aX + b, a > 0$

#### Relation between autocovariance and autocorrelation

- ![](/assets/images/2022-02-08-07-24-18.png)
- K is autocorvaiance and R is autocorrelation

<blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em"><b>Uncorrelated does not imply independence</b><br>Corrleation only measure linear dependency. So the data can be completely dependent but may have 0 correlation</blockquote>

<blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em">Correlation does not imply causation</blockquote>

### Simpson's Paradox

![](/assets/images/2022-02-08-07-31-20.png)

- trends shown by small groups of data can disappear or reverse when the groups are combined
  - in small groups, y increases with x, but overall y decreases with x