# SDFs

> signed distance functions



For a volume $\mathcal{M} \sim \mathbb{R}^3$

we want to get its surface $\mathcal{S}$



SDFs are functions $f: \mathbb{R}^3 \mapsto \mathbb{R}$ where $d = f(x)$ is the shortest signed distance from a point $\mathbf{x}$ to the surface

sign indicates whether $\mathbf{x}$ is inside or outside of 



学出很多登高面，然后0登高面就是表面

zero level-set



![image-20210219111025930](https://raw.githubusercontent.com/yzy1996/Image-Hosting/master/20210219111027.png)

Humans possess an impressive intuition for 3D shapes: given partial observations of an object we can easily imagine the shape of the complete object. Now we want to reproduce this ability with algorithms.



### DeepSDF

[Deepsdf Learning continuous signed distance functions for shape representation](https://arxiv.org/abs/1901.05103)

**[`CVPR 2019`]**	**[`UW, MIT,Facebook`]**

**[`Jeong Joon Park`, `Peter Florence`, `Julian Straub`, `Richard Newcombe`, `Steven Lovegrove`]**

<details><summary>Click to expand</summary><p>


> **Summary**

They propose a training stabilizer based on **consistency regularization**. In particular, they **augment data** passing into the GAN discriminator and **penalize the sensitivity** of the discriminator to these augmentations.

> **Details**

(from [DIT]())

It defines a surface as the level set of a signed distance field (SDF), e.g. $\mathcal{F}(\boldsymbol{p})=0$, where $\boldsymbol{p} \in \mathbb{R}^3$ donates a 3D point and $\mathcal{F}: \mathbb{R}^3 \mapsto \mathbb{R}$ is a function approximated using a deep neural network.

In practice, in order to represent multiple object instances using one neural network, the function $\mathcal{F}$ also takes a condition variable $\boldsymbol{c}$ as input and thus can be written as:
$$
\mathcal{F}(\boldsymbol{p}, \boldsymbol{c})=s: \boldsymbol{p} \in \mathbb{R}^{3}, \boldsymbol{c} \in \mathcal{X}, s \in \mathbb{R}
$$
The object surface can be extracted using [Marching Cube]().



$\boldsymbol{c}$ is a high-dimensional latent code and each shape instance has a unique code. All latent codes are firstly initialized with Gaussian noise and then optimized in parallel with network training.



</p></details>

---

### MetaSDF

[MetaSDF: Meta-learning Signed Distance Functions](https://arxiv.org/pdf/2006.09662.pdf)

**[`NeurIPS 2020`]**	**(`Stanford`)**

**[`Vincent Sitzmann`, `Eric R. Chan`, `Richard Tucker`, `Noah Snavely`, `Gordon Wetzstein`]**

a dataset $\mathcal{D}$ of $N$ shapes, each shape is represented by a set of points $X_i$ consisting of $K$ point samples


$$
\mathcal{D} = \{X_i\}_{i=1}^N, \qquad X_i = \{(\mathbf{x}_j, s_j):s_j = SDF_i(\mathbf{x}_j)\}_{j=1}^K
$$
where $\mathbf{x}_j$ are spatial coordinates, and $s_j$ are the signed distances at these spatial coordinates

