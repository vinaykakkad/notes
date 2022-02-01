---
id: ei9JWoeceRbHDcPoNblcb
title: Lec 6
desc: ''
updated: 1643746611893
created: 1643607271875
---

# Curse of Dimensionality

- as the dimension increases, the volume of space grows exponentially
- *thus we need to look farther to find the nearest neighbour*

## Unit cube example 

- we create a space with a constant $n$ number of points, degree $d$ and length 1
  - $\implies point\hspace{1mm}density = \frac{n}{1^d} = n$
- we consider another cube with side $s$ 
  - thus the number of points inside this cube is $n*s^d$
- if we want to find k nearest neighbors, then the length of the cube should be:
  - $n*s^d = k$
  - $\boxed{s = (\frac{k}{n})^{(\frac{1}{d})}}$
- if plot take $k=1$ and find the values of $d$ vs $s$
  - ![](/assets/images/2022-02-02-01-29-18.png) 
  - i.e. for finding nearest neighbor we have to look at almost the edge of our space
  - **_in higher dimension, the notion of neighbour is violated_**

<details>
<summary>another view point</summary>

- ![](/assets/images/2022-02-02-01-43-31.png)
- [ ] [code](https://github.com/probml/pyprobml/blob/master/scripts/curse_dimensionality_plot.py) 

</details>

## Implications

- as $d$ increases, volume of the space increases and data becomes *sparser*
- to get reliable results, data needs to get exponentially
- *in high dimension space, objects are sparse and dissimilar*
- provides motivation for dimensionality reduction techniques like PCA and many more