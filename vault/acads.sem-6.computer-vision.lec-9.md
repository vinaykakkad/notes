---
id: PezPhIacmef48kh1E5p9d
title: Lec 9
desc: ''
updated: 1644344196076
created: 1644305421621
---

## Second moments of a region

- to find the parameters $\lambda_1$ and $\lambda_2$, we use *second moments*
- we take a window $W$ centered at a pixel, and compute 3 parameters
  - $a = \sum_{i\in W} (I_{x_i})^2$ - sum of intensity in x-direction
  - $b = 2 \sum_{i\in W} (I_{x_i}^2 * I_{y_i}^2)$ - sum of product of intensities in x and y direction
  - $c = \sum_{i\in W} (I_{y_i})^2$ - sum of intensity in y-direction
- The length of the parameters, semi-major axis $\lambda_1$ and semi-min axis $\lambda_2$ can be calculated as:
  - $\lambda_1 = E_{max} = \frac{1}{2} [a + c + \sqrt{b^2 + c^2 + (a-c)^2}]$
  - $\lambda_2 = E_{min} = \frac{1}{2} [a + c - \sqrt{b^2 + c^2 + (a-c)^2}]$
- based on the values of $\lambda_1$ and $\lambda_2$, we can classify into
  - $\lambda_1 \backsim \lambda_2,\; both \; are \; small \implies flat\hspace{1mm}region$
  - $\lambda_1 >> \lambda_2 \implies edge\hspace{1mm}region$
  - $\lambda_1 \backsim \lambda_2,\; both \; are \; large \implies corner\hspace{1mm}region$

### Harris Corner Detection

![](/assets/images/2022-02-08-17-34-46.png)
- plotting the $\lambda_1 vs \lambda_2$ distribution, we can find the regions for different types of surfaces

<br>

- Harris defines $R = \lambda_1 \lambda_2 - K(\lambda_1 + \lambda_2)^2$, $0.04 < K 0.05$
- Thus we get a single boundary for detecting corners

#### Non Maximal Supression

![](/assets/images/2022-02-08-21-15-19.png)
- after detecting the cornes using a single threshold, we generally get a cluster of corners
- we use non-maximal supression to reduce false positives
  - we slide a *window* k over the image
  - at each position, if the pixel at the center is not maximum we supress it and only reatin those which are maximum
  
# Boundary Detection

- fit the object boundaries from the edge pixels
  - fit lines or curves to the edges
  - active contours(*snakes*)
  - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">Hough Transform</code>
- some preprocessing is performed to improve the quality
  - i.e. filtering out some oultiers or noisy pixels
<details>
<summary>preprocessing process</summary>

![](/assets/images/2022-02-08-14-04-15.png)

</details>

## Fitting lines and curves to edges

![](/assets/images/2022-02-08-21-24-37.png)
- we define the error function(veritcal distance) as
- $\frac{1}{n}\sum_i (y_i - m*x_i - c)^2$
- for minmizing the error, we take partial derivatives with respect to m and c, and set them to 0
- $m = \frac{\sum_i (x_i - \bar{x})(y_i - \bar{y})}{\sum_i (x_i - \bar{x})^2}, \hspace{1mm} c = \bar{y} - m\bar{x}$

# Extendel Learning / TODO

- [ ] If the points are oriented vertically, how do we find the vertical distance
