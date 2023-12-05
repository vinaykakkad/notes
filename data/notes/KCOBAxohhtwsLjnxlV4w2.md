
## Canny edge detection steps in detail

- smoothing with 2D gaussain filter - $n_{\sigma} * I$
- compute image gradient using *sobel* operator - $\nabla n_{\sigma} * I$

<details>
<summary>find the magnitude and direction of the gradient</summary>

![](/assets/images/2022-02-08-23-31-51.png)
- brighter the point, higher the magnitude
- direction is given by the green arrow

</details>

<details>
<summary>compute the <i>laplacian</i> along the direction of gradient</summary>

![](/assets/images/2022-02-08-23-34-58.png)
- instead of the normal 2D laplacian, canny used a 1D laplacian along the direction of the gradient

</details>

- apply non maximum supression to remove false positives
- apply hysteresis threshold

<details>
<summary>canny edge detection results</summary>

![](/assets/images/2022-02-08-23-44-44.png)

</details>

# Corner 

![](/assets/images/2022-02-03-13-53-42.png)
- rapid change of intensity in two direction within a small region or meeting of two edges

## Corner Detection

<details>
<summary>gradients for flat, edge and corner region</summary>

![](/assets/images/2022-02-03-14-04-14.png)

</details>

- plotting the distribution of $I_x$ and $I_y$, we get
- ![](/assets/images/2022-02-03-14-16-17.png)
  - these elliptical distributions can be *parmaterized* based on the *semi-minor axis* and *semi-major axis* of the ellipses
    - $\lambda_1: semi\,major\,axis$
    - $\lambda_2: semi\,minor\,axis$

# TODO

- [ ] non maximal supression, hystersis threshold and its code 