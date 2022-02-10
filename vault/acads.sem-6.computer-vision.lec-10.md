---
id: s9k71a9JQIZGzZjsXUmWR
title: Lec 10
desc: ''
updated: 1644483197212
created: 1644478289786
---

## Fitting a curve to edges

![](/assets/images/2022-02-10-13-39-39.png)
- we need to find the polynominal which minimizes the perpendicular distance
- $E = \frac{1}{N} \sum_i (y_i - ax_i^3 - bx_i^2 - cx_i - d)$
  - we solve linear(linear function of parameters) system of equations using *least squares*
  - we find the *partial derivative* with respect to all the params and set it to zero to find the minima

<br>

- we need to determine the *degree* of the polynomial that best fits the given edges
  - as the number of params is very less comprared to the number of equation, get a **_over-determined_** linear system
- rearraning these equation into a matrix form, we get
- ![](/assets/images/2022-02-10-13-53-14.png)
- finding the moore penrose *pseduo-inverse* for this system of equation, we get the least squares solution
- ![](/assets/images/2022-02-10-13-59-30.png)

# Active Contours(Snakes)

![](/assets/images/2022-02-10-14-04-21.png)
- iterativel deforms initial contours unitl:
  - it is near the pixel with *high gradients* (edges)
  - it is smooth

## Representing a contour

![](/assets/images/2022-02-10-14-10-25.png)
- contour is described using a ordered list of 2d vertices(control points)
- lines connecting the *control points*

## Attracting contours to edges

![](/assets/images/2022-02-10-14-18-51.png)
- we attract the contour by maximizing the sum of *gradient magnitude square*
- this is process is knows as <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">boundary tracking</code>