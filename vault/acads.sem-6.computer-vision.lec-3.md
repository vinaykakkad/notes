---
id: Y2iLGKl9mabCkYXe9njir
title: Lec 3
desc: ''
updated: 1643292614960
created: 1643183477024
---

# Camera Calibration

- we take an object of known geometry and its image map the correspoding points
![](/assets/images/2022-01-27-19-04-05.png)
- mapping more points and rearrangin into a matrix we get:
![](/assets/images/2022-01-27-19-06-21.png)
- thus we get an equation of the form $AP = 0$
- we are in the *homogeneous system*, and scaling the coordinates gives us the same *cartesian coordinates*
  - thus we can set $\lvert\lvert P \rvert\rvert^2$ to any arbitrary value
  - we set $\lvert\lvert P \rvert\rvert^2 = 1$ for mathematical convenience 
  
## Constrained Least  Squares

- thus we need to find the solution for $AP = 0$ such that $\lvert\lvert P \rvert\rvert^2 = 1$
  - this problem is known as <code style="background-color: #43b02a40; padding:3px 2px; border-radius: 5px">constrained least-squares</code>
  - i.e. $\begin{matrix}min\\ p\end{matrix} \lvert\lvert AP \rvert\rvert^2$ such that $\lvert\lvert P \rvert\rvert^2 = 1$
- to find best approximate solution, we try to minimize the loss function 
$$
l(P, \lambda) = (AP)^TAP - \lambda(P^TP-1)
$$
- taking the derivate and setting to $0$ to minimize, we get 
$$
2AP - 2\lambda P = 0 \implies \boxed{AP = \lambda P}
$$
- **_Eigen vector corresponding to smallest eigenvalue gives us P_**

## Finding the intrinsic and extrinsic parameters

- using the properties of calibration matrix and rotation matrix, we can find them using the *QR decomposition* of the first 3 cols of *projection matrix* P 
- ![](/assets/images/2022-01-27-19-38-51.png)
