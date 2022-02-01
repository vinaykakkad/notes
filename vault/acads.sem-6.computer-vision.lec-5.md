---
id: BgB9oRCh7UiA8oSQuR6Ly
title: Lec 5
desc: ''
updated: 1643537962825
created: 1643521022646
---
# Edge Detection using Gradients

<details>
<summary>gradient plots</summary>

![](/vault/assets/images/2022-01-30-11-22-19.png)

</details>

- we want to detect *rapind change* in intensity, therefore we find the gradient of the image 
- local maximas $\implies$ position of the edges 
- height of the local $\implies$ maxima strength of the edges
- for detecting edges in a 2d space, we use *partial derivate* 
$$
\nabla I = [\frac{\delta I}{\delta x}, \frac{\delta I}{\delta x}]
$$
- *gradient magnitue*: $S=\sqrt{(\frac{\delta I}{\delta x})^2 + (\frac{\delta I}{\delta x})^2}$ and *gradient direction*: $\theta = tan^{-1}(\frac{\delta I}{\delta x} / \frac{\delta I}{\delta x})$

## Finite differences for matrices

- as the image has discrete intensity values for pixel, we find the finite differences 
- ![](/vault//assets/images/2022-01-30-15-36-15.png)
- this operations can be expressed in the form of <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">kernels</code>

### Kernel examples

![](/vault/assets/images/2022-01-30-15-39-17.png)
<details>
<summary>smoothing vs localisation example</summary>

![](/vault/assets/images/2022-01-30-15-46-09.png)

</details>

- **_As the size of kernel increases, smoothness increases and localisation decreases, noise sensitivity decreases_**