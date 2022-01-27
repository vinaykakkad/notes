---
id: jnYmiJo5s2BuF2CYJe4b1
title: Lec 1
desc: ''
updated: 1643204263155
created: 1642880549600
---
# Computer Vision

- ![computer vision](/assets/images/2022-01-20-11-22-17.png)
- light(simple point source or any other complex sytem) falls on a scene and gets scattered and reflected
- camera captures this light by digitalizing the light intensity
  - *sampling* and *quantization* are involved
  - image is then represented as matrix of these values (*pixels*)
- a computer vision derives some information from this and gives scence description

# Image formation model

- how a 3d object is projected onto a 2d image plane
- we understand this to later reconstruct some information from a 2d image

## Perspective projection with Pinhole

![](/assets/images/2022-01-25-10-21-43.png)
- the image of a point $P_o$ with position vector $\overrightarrow{r_o} = (x_o, y_o, z_o)$ gets projected on the image plane at point $P_i$ with position vector $\overrightarrow{r_i} = (x_i, y_i, f)$
- from the similarities of triangle we get:
$$
\frac{\overrightarrow{r_i}}{f} = \frac{\overrightarrow{r_o}}{z_o} \implies \frac{x_i}{f} = \frac{x_o}{z_o}\hspace{2mm},\hspace{2mm} \frac{y_i}{f} = \frac{y_o}{z_o}
$$
- these equations are known as *equations of perspective projection*

### Properties of perspective projection

- straign line in the scene remains a straight line in the image
- maginification $m$ is give by $m = \frac{f}{z_o}$
  - reason for point intersecting at infinity

## Linear Camera Model

- mapping the 3D points into 2D image plane
- also known as *forward imaging model*
![](/assets/images/2022-01-25-12-11-10.png)
- the image formed depends on:
  - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">Extrinsic Parameter</code> - orientation of camera with respect to the object in the 3D world (*world coordinate frame*)
  - <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">Intrinsic Parameter</code> - how the camera maps the 3D coordinates of the object on an 2D image plan(internal parameters of the camera)
- in the forward imaging model: 
  - ![](/assets/images/2022-01-25-12-22-12.png)
  - world coordinates of a point $X_w = [x_w y_w z_w]^T$(**_position vector with respect to the world coordinate system_**) gets transformed to camera coordinates $X_c = [x_c y_c z_c]^T$(**_position vector with respect to the camera coordinate system_**)
  - this camera coordinates get mapped on the image plane $X_i = [x_i, y_i]^T$ using the perspective projection

### Camera to image transformation

- using the *equations of perspective projection*, we can find the relation between image coordinates and the camera coordinates
$$
\frac{x_i}{f} = \frac{x_c}{z_c}\hspace{2mm},\hspace{2mm} \frac{y_i}{f} = \frac{y_c}{z_c}
$$

#### Image plane to image matrix

![](/assets/images/2022-01-25-17-06-05.png)
- the image plane is continuous, but the matrix give by the light sensors is discrete
- if we consider the *density*(pixels/mm) of pixels in the  $\hat{x}$ and $\hat{y}$ direction as $m_x$ and $m_y$ and number of pizels be $u$ and $v$, then we can relate them by:
$$
u = m_x x_i \hspace{2mm},\hspace{2mm} v = m_y y_i
$$
- using the equations between image and camera corrdiantes, we get
$$
u = m_x f \frac{x_c}{z_c} \hspace{2mm},\hspace{2mm} v = m_y f \frac{y_c}{z_c}
$$
- the origin of the image sensor may be at the center, thus we consider a <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">principle point</code> with the pixel $(o_x, o_y)$ and the final equation is given by:
$$ 
u = f_x \frac{x_c}{z_c} + o_x \hspace{2mm},\hspace{2mm} v = f_y \frac{y_c}{z_c} + o_y
$$
^dAINqR5UIUcW
- $f_x$ and $f_y$ are the effective focal length in pixels, in the $\hat{x}$ and $\hat{y}$ direction
