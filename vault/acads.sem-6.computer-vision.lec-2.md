---
id: kFdhjexbkBPW1a47YdOKh
title: Lec 2
desc: ''
updated: 1644747842768
created: 1643181184689
---

[Homogeneous Coordinates](http://www.songho.ca/math/homogeneous/homogeneous.html)

## Using Homogeneous Coordinates to get a linear equation
![[dendron:Lec 1|acads.sem-6.computer-vision.lec-1#^dAINqR5UIUcW]]
- to remove the non-linearity in the above equations, we use the homogeneous coordinates of the image point $(u, v)$
  - we bump the dimension using scalar $z_c$ to get rid of the denominator
$$
\begin{pmatrix}
\hat{u} \\ \hat{v} \\ \hat{w} 
\end{pmatrix} \equiv 
\begin{pmatrix}
\hat{z_cu} \\ \hat{z_cv} \\ \hat{z_c} 
\end{pmatrix} =
\begin{pmatrix}
{f_xx_c + o_xz_c} \\ {f_yy_c + o_yz_c} \\ {z_c} 
\end{pmatrix}
$$
- to capture the transformation from camera coordinate $[x_c\hspace{2mm}y_c\hspace{2mm}z_c\hspace{2mm}1]$ to the image coordinate $[\hat{u}\hspace{2mm}\hat{v}\hspace{2mm}\hat{w}]$, we use a single 3x4 matrix
$$
\begin{pmatrix}
\hat{u} \\ \hat{v} \\ \hat{w} 
\end{pmatrix} = 
\begin{pmatrix}
f_x&0&o_x&0 \\ 0&f_y&o_y&0 \\ 0&0&1&0
\end{pmatrix}
\begin{pmatrix}
x_c\\y_c\\z_c\\1
\end{pmatrix}
$$
- this matrix is known as matrix of intrinsic properties $M_{int}$ and the inner 3x3 matrix is knows as *calibration matrix* $K$
  - i.e. $M = [K\hspace{2mm}0]$ 
  - **_K is an upper triangular matrix_**

# World Coordinate to Camera Coordinate

- this tranfomration is a change of coordinate system and can be characterized by an **_orthonormal_** rotation matrix $R$ and a translation vector $\overrightarrow{t}$
$$
\begin{pmatrix}
x_c\\y_c\\z_c
\end{pmatrix} = 
\begin{pmatrix}
r_{11} & r_{12}&r_{13}\\ r_{21}&r_{22}&r_{23}\\ r_{31}&r_{32}&r_{33}
\end{pmatrix}
\begin{pmatrix}
x_w\\y_w\\z_w
\end{pmatrix} + 
\begin{pmatrix}
t_x\\t_y\\t_z
\end{pmatrix} 
$$
- this can be rewriiten in homogeneous system as
$$
\begin{pmatrix}
x_c\\y_c\\z_c\\1
\end{pmatrix} = 
\begin{pmatrix}
r_{11} & r_{12}&r_{13}&t_x\\ r_{21}&r_{22}&r_{23}&t_y\\ r_{31}&r_{32}&r_{33}&t_z\\0&0&0&1
\end{pmatrix}
\begin{pmatrix}
x_w\\y_w\\z_w\\1
\end{pmatrix}  
$$
- this in knows as *matrix of external parameters* $M_{ext}$ and $M_{ext} = \begin{pmatrix}R&t\\0&1\end{pmatrix}$
- the projection vector $P$ can be expressed as $P = M_{int}M_{int}$
