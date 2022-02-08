---
id: U9lUxkH7Gix1SnSBfN7bb
title: Lec 7
desc: ''
updated: 1644344196078
created: 1644336629713
---

# Gaussian Smoothing

<details>
<summary>smoothing using gaussian convolution</summary>

![](/assets/images/2022-02-08-21-52-43.png)

</details>

- we use gaussain smoothing to supress the noice by convolving the gaussian
- to save computation power, instead of first smoothening out image and then finding the derivate to find edge, 
  - we apply the differentiation on the gaussain filter and then applied the combined filter on the image
  - *this is because the convolution function associativity*
  - this is knows as <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">LoG</code> (*laplacian of gaussian*)
- *PRINCIPLE*: gaussian assign a high value to the central input and also considers the **neighboring** inputs

<details>
<summary>gradient vs laplacian</summary>

![](/assets/images/2022-02-08-22-10-39.png)
![](/assets/images/2022-02-08-22-11-00.png)

</details>

# Canny Edge Detection

- combining good points from sobel and laplacian

## objective

- good detection: true edges, and minimal false positives
- good localisation: sub pixel level accuracy
- single point constrains: only one point corresponding to edge point

## Steps

1. smoothing with 2D gaussain filter
2. compute image gradient using *sobel* operator
3. find magnitude and orientation of gradient at each pixel
4. compute the *laplacian* along the direction of gradient
5. apply non maximum supression to remove false positives
6. apply hysteresis threshold