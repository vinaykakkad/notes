# Thresholding

- ![](/assets/images/2022-01-30-15-52-25.png)
- thresholding helps us to get a sharper edge and get a better idea of shape
- a simple approach would be to fix a bound and perform binary classification(edge, non-edge)

## Hysteresis Thresholding

- if the gradient at a pixel is:
  - above *high threshold* $T_h$, classify it as **edge**
  - below *low threshold* $T_l$, classify it as **non-edge**
  - for any pixel in between
    - iteratively classify based on the neighbors

### Implementation

- $T_h:T_l = 1:2\hspace{1mm}or1:3$
- select $T_h$ such that edges cannot be ignored - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">seed points</code>
- from the seed move to the *8-neighborhood* as long as the pixels does not fall below $T_l$

# Edge Detection using Second Derivative

<details>
<summary>edge derivative plots</summary>

![](/assets/images/2022-02-01-12-03-57.png)

</details>

- first derivative gives us the strength and direction
- second derivative is used to detect *polarity*
- *zero crossing* indicates the presence of edge and can locate thick edges

## Discrete lapacian operator

- finite differences of second order are given given by the <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">del square</code> ($\nabla_2 I$)
<details>
<summary>formulae for del-square</summary>

![](/assets/images/2022-02-01-16-03-54.png)

</details>

### Implementation

- ![](/assets/images/2022-02-01-16-05-17.png)
- this can be implemented using the convolution masks:
- ![](/assets/images/2022-02-01-16-28-48.png)
- when we appy this convolution masks, the convoluted matrix contains negative values
  - when plotting this image without normalising, we get an image where negative values give a blackish pixels, 0 gives greyish pixel and positive values gives brighter pixels
  - therefore before plotting the final image, we need to normalize it to get a prope image

# Effect of noise

![](/assets/images/2022-02-01-12-19-45.png)
- if the noise increases, it becomes difficult to differentiate between noise and edge as the derivate detects rapid change

<br>

- noise in the image is almost invisible 
- but *difference filters* respond very strongly to noise
- noise changes the neighborhood and the outcome is very different
- solutions
  - if the frequency is high, remove using low pass filter
  - use kernels of higher size to decrease noise sensitivity